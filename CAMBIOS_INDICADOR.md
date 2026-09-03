# Cambios del indicador — `SMC_Sniper_XAUUSD.pine` (v2)

Versión alineada al [Plan de Trading](PLAN_DE_TRADING.md). Copia el `.pine` en el
editor Pine de TradingView y añádelo al gráfico de XAUUSD.

> **Últimos ajustes:** RR por defecto **2.0** (profit $100 con riesgo $50). Panel de estado
> con **tamaño configurable** (Auto / Normal / Grande / Enorme) y **posición configurable**;
> `Auto` escala el texto según la pantalla, adaptándose a PC y celular.

## 0. Ajustes anti-stop (v2.4)

Para reducir los SL por perseguir impulsos con stops cortos (típico en las
parabólicas del oro):

- **SL por ATR más amplio:** múltiplo por defecto **1.5** (antes 1.0). Da aire al
  stop para que el ruido/mechas no te saquen; a cambio el lote baja (bien para fondeo).
- **Filtro anti-persecución (nuevo, ON):** rechaza la señal si la vela del gatillo
  (o la anterior) es un impulso grande — rango > **1.5 × ATR**. Evita entrar al final
  de un movimiento parabólico justo antes del retroceso. Configurable en "🎯 Sniper Settings".
  El diagnóstico muestra "Vela de impulso (anti-persecución)" cuando bloquea una señal.

## 1. Defectos corregidos

| Defecto detectado | Corrección |
|---|---|
| Una señal nueva **sobrescribía** una operación abierta (reseteaba SL/TP y el monitor). | La compuerta del plan exige `not inTrade_sn`: no hay nueva entrada mientras haya una operación viva. |
| Señales desconectadas de la estructura (filtros SMC/ADX en OFF y marcados "NO recomendado"). | `use_adx_sn` y `use_smc_trend_sn` ahora vienen **activados** y reetiquetados como *recomendado*. Solo dispara a favor de tendencia y fuera de rangos. |
| Sin límites de disciplina (operaba sin parar). | Gestión diaria completa (ver abajo). |
| P&L sin costos. | Nuevo input **Costo por operación** (spread+comisión) que se descuenta del resultado. |
| Meta flotante en $400 (inalcanzable con el riesgo del plan). | Ahora avisa a ~$90 para **mover el SL a breakeven** a mitad de camino del TP. |

## 2. Gestión diaria según el plan (grupo "📋 Gestión según Plan de Trading")

- **Máximo de operaciones por día:** 2 (configurable 1–5).
- **Detener el día tras ganar:** si una operación llega al TP, no se toman más entradas ese día (meta cumplida).
- **2ª entrada solo tras pérdida:** si la 1ª pierde, se permite una segunda (y última) entrada. Si la 1ª gana, se cierra el día.
- **Panel de estado (HUD)** arriba a la derecha: operaciones usadas, pérdidas, P&L del día y estado (🟢 Operable / 🟡 En operación / ✅ Meta del día / ⛔ Límite).

## 3. Riesgo por % de la cuenta (v2.1 — corrige el sobre-apalancamiento)

**Problema detectado:** un riesgo fijo de `$100` en una cuenta de **$5.000 es el 2%**, no el 1%,
y forzaba lotes altos (0.10) con SL cortos de M15. Ahora el riesgo se calcula como **% del
tamaño real de la cuenta**, por lo que se adapta solo.

- **Tamaño de la cuenta ($):** `5000` por defecto.
- **Riesgo como % de la cuenta:** `ON` (recomendado).
- **Riesgo por operación (%):** `1.0` → **$50** en una cuenta de 5k. Usa `0.5%` ($25) para fondeo estricto.
- **Lote máximo permitido:** `0.20` (tope de seguridad para SL muy cortos).
- **El beneficio es determinista:** `Profit = Riesgo × RR`.

| Cuenta | Riesgo % | Riesgo $ | RR | Beneficio |
|---|---|---|---|---|
| 5.000 | 1.0% | $50 | 1.5 | **$75** |
| 5.000 | 1.0% | $50 | 2.0 | **$100** |
| 5.000 | 0.5% | $25 | 2.0 | **$50** |
| 10.000 | 1.0% | $100 | 1.5 | **$150** |

> ⚠️ **Fondeo:** con drawdown diario típico ~5% ($250 en 5k), 2 operaciones a 1% ($50) arriesgan
> $100/día. A 2% ($100) rozarías el límite. Mantén 0.5%–1%.
>
> Para un beneficio fijo, deja **OFF** "Ajustar lote según fuerza de la señal" (en ON reduce
> lote/riesgo/beneficio en señales débiles).

## 4. Cálculo del lote

`lote = riesgo / (distancia_SL_en_$ × 100)`, con tope configurable (`0.20` por defecto).
Es correcto para XAUUSD estándar (100 oz → $100 por cada $1 de movimiento por lote).
El SL usa **ATR × 1.0** por defecto (distancias consistentes), por lo que el profit en $
sale siempre igual a `Riesgo × RR` independientemente de la volatilidad.

> **SL corto en M15:** cuanto más ajustado el SL, mayor el lote para el mismo riesgo en $.
> Si quieres lotes más pequeños, sube el múltiplo ATR del SL (1.5) o busca entradas con más
> recorrido. El tope de lote evita que un SL muy corto dispare el tamaño.

## 5. Sesiones Londres y New York (independientes)

En el grupo **"🕐 Sesiones (horario Colombia, UTC-5)"** hay **dos bloques separados**, cada uno
con su propio cupo de operaciones y sus propios contadores:

| Sesión | Ventana por defecto (COL) | Cupo | Reglas |
|---|---|---|---|
| 🇬🇧 Londres | **02:00 – 08:00** | **2** | Para si gana · 2ª entrada solo tras pérdida |
| 🇺🇸 New York | **08:00 – 16:00** | **2** | Igual, independiente de Londres |

- Son **independientes**: si un día no operas en Londres, New York conserva sus 2 entradas.
- Cada sesión aplica por separado "detener al ganar" y "2ª entrada tras pérdida".
- Puedes **desactivar** una sesión con su casilla, o cambiar horas y cupo.
- El **panel HUD** muestra una fila por sesión (`🇬🇧 Londres 1/2`, `🇺🇸 New York 0/2`),
  resalta la sesión activa y marca ✅ (meta) o ⛔ (cupo agotado).

> ⏰ **Horario de verano (DST):** los valores están en hora Colombia (UTC-5) para horario
> estándar. En verano de EE.UU./Europa resta ~1 hora a las ventanas. Ajusta las horas si ves
> que las señales caen fuera de la sesión real.

---

⚠️ El P&L y los resultados dibujados son una **simulación visual** (usan high/low intrabar).
No son un backtest de broker. Valídalo primero en **cuenta demo** siguiendo el plan.
