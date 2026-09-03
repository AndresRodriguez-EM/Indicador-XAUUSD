# Cambios del indicador — `SMC_Sniper_XAUUSD.pine` (v2)

Versión alineada al [Plan de Trading](PLAN_DE_TRADING.md). Copia el `.pine` en el
editor Pine de TradingView y añádelo al gráfico de XAUUSD.

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

## 5. Horario

Por defecto **06:00–11:00 hora Colombia** (solape Londres/NY, la mejor ventana del oro).
Ajústalo en el grupo "🎯 Sniper Settings".

---

⚠️ El P&L y los resultados dibujados son una **simulación visual** (usan high/low intrabar).
No son un backtest de broker. Valídalo primero en **cuenta demo** siguiendo el plan.
