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

## 3. Riesgo y beneficio según el plan

- **Riesgo por operación:** `$100` por defecto (1%). Cámbialo a `75` si es lo que arriesgas.
- **RR:** `1.5` por defecto.
- **El beneficio es determinista:** `Profit = Riesgo × RR`.

| Riesgo | RR | Beneficio |
|---|---|---|
| 100 | 1.5 | **$150** |
| 100 | 1.8 | **$180** |
| 95 | 2.0 | **$190** |
| 75 | 2.0 | **$150** |

> Para mantener el beneficio fijo del plan, deja **OFF** "Ajustar lote según fuerza de la señal".
> Con esa opción en ON el lote (y por tanto el riesgo y el beneficio) se reduce en señales débiles.

## 4. Cálculo del lote

`lote = riesgo / (distancia_SL_en_$ × 100)`, con tope de `0.50` lotes.
Es correcto para XAUUSD estándar (100 oz → $100 por cada $1 de movimiento por lote).
El SL usa **ATR × 1.0** por defecto (distancias consistentes), por lo que el profit en $
sale siempre igual a `Riesgo × RR` independientemente de la volatilidad.

## 5. Horario

Por defecto **06:00–11:00 hora Colombia** (solape Londres/NY, la mejor ventana del oro).
Ajústalo en el grupo "🎯 Sniper Settings".

---

⚠️ El P&L y los resultados dibujados son una **simulación visual** (usan high/low intrabar).
No son un backtest de broker. Valídalo primero en **cuenta demo** siguiendo el plan.
