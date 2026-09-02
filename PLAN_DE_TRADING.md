# Plan de Trading — XAUUSD (Oro)

> Documento vivo. Revísalo y ajústalo cada mes con base en tus resultados reales.
> **Aviso:** Esto es material educativo, no asesoría financiera. El trading con
> apalancamiento puede provocar la pérdida total del capital. Nunca operes con
> dinero que no puedas permitirte perder.

---

## 1. Por dónde empezar (orden recomendado)

1. Define tu **objetivo** y tu **perfil de riesgo** (sección 2).
2. Elige tu **horario** y tu **temporalidad** (secciones 4 y 5).
3. Define **1 sola estrategia/setup** y opéralo hasta dominarlo (sección 6).
4. Fija tus **reglas de gestión de riesgo** — esto es lo más importante (sección 7).
5. Practica en **cuenta demo** mínimo 20–30 sesiones registrando todo (sección 10).
6. Pasa a **cuenta real pequeña** solo cuando seas rentable y consistente en demo.

> Regla de oro: **primero sobrevivir, después ser rentable.** La gestión de riesgo
> importa más que el punto de entrada.

---

## 2. Objetivos y perfil

| Concepto | Tu definición |
|---|---|
| Capital de la cuenta | _______ USD |
| Riesgo máximo por operación | 0.5 % – 1 % del capital |
| Riesgo máximo diario | 2 % – 3 % (si se alcanza, se cierra el día) |
| Pérdida máxima semanal | 5 % – 6 % (si se alcanza, se para la semana) |
| Objetivo mensual realista | 3 % – 8 % (NO fijes metas de "duplicar la cuenta") |
| Nº máx. de operaciones/día | 2 – 3 (calidad > cantidad) |
| Estilo | Intradía / Scalping / Swing (elige uno) |

---

## 3. Conoce el activo: XAUUSD

- **Qué es:** Onza de oro cotizada en dólares. Muy líquido y con alta volatilidad.
- **Se mueve por:** DXY (índice dólar), tasas de interés y datos de la FED,
  inflación (CPI/PCE), datos de empleo (NFP), riesgo geopolítico y aversión al riesgo.
- **Correlación clave:** Suele moverse **inverso al dólar (DXY)** y a los rendimientos
  reales de los bonos. Si el DXY sube fuerte, el oro tiende a bajar.
- **Volatilidad:** Puede recorrer cientos de "pips" en minutos durante noticias.
  El valor del pip y el tamaño del contrato cambian según el bróker: **verifícalo**.

---

## 4. Horarios de operación (hora del servidor/UTC — ajústalos a tu zona)

| Sesión | Ventana aprox. (UTC) | Comportamiento del oro |
|---|---|---|
| Asia | 00:00 – 07:00 | Rango, baja volatilidad |
| **Londres** | 07:00 – 11:00 | Alta volatilidad, buenos movimientos |
| **Solape Londres/NY** | 12:00 – 15:00 | **La mejor ventana** (mayor volumen) |
| Nueva York | 12:00 – 20:00 | Volatilidad alta, sensible a noticias |

**Regla:** No abrir operaciones nuevas 15 min antes/después de noticias de alto
impacto (NFP, CPI, decisiones de la FED). Consulta un calendario económico a diario.

---

## 5. Temporalidad (multi-timeframe)

- **Tendencia / contexto:** H4 y H1 → ¿alcista, bajista o rango?
- **Estructura / niveles:** M15 → zonas de soporte/resistencia, order blocks, liquidez.
- **Entrada / gatillo:** M5 o M1 → confirmación de entrada.

> Nunca operes contra la tendencia del marco superior sin una razón muy sólida.

---

## 6. Estrategia y setup (elige UNO para empezar)

Documenta tu estrategia con reglas objetivas. Ejemplo de plantilla:

**Setup: Retroceso a zona en tendencia**
- **Condición previa:** Tendencia clara en H1 (máximos/mínimos crecientes o decrecientes).
- **Zona:** Precio regresa a un soporte/resistencia o zona de valor (Fibonacci 0.5–0.618,
  media móvil, order block).
- **Gatillo de entrada:** Vela de confirmación en M5 (envolvente, rechazo/mecha, ruptura
  de micro-estructura a favor de la tendencia).
- **Confluencias mínimas requeridas (≥2):** estructura + zona + confirmación de vela
  + (opcional) DXY a favor.
- **Invalidación:** Si el precio cierra más allá de la zona → no hay entrada / se sale.

> Escribe TUS reglas aquí de forma que otra persona pudiera ejecutarlas sin dudar.
> Si no puedes describir el setup con reglas claras, aún no estás listo para operarlo.

---

## 7. Gestión de riesgo (lo más importante)

- **Riesgo por operación:** máximo 1 % del capital. Se calcula ANTES de entrar.
- **Stop Loss (SL):** obligatorio y colocado en un nivel lógico (detrás de la zona/
  estructura), NO a una distancia arbitraria.
- **Take Profit (TP):** relación **Riesgo:Beneficio mínima de 1:1.5**, ideal 1:2 o más.
- **Tamaño de posición (lotaje):**

  ```
  Riesgo en $ = Capital × % de riesgo
  Lotaje = Riesgo en $ / (distancia del SL en pips × valor del pip por lote)
  ```

  Ejemplo: Capital 1.000 $, riesgo 1 % = 10 $. SL de 50 pips, valor pip 1 $/lote (0.01).
  → Lotaje ≈ 10 / (50 × 1) = **0.2** (usa siempre los valores reales de tu bróker).

- **Nunca** muevas el SL en contra para "darle espacio". Sí puedes moverlo a favor
  (a break-even / trailing) cuando la operación avanza.
- **Prohibido promediar pérdidas** (añadir a una posición perdedora).

---

## 8. Gestión de la operación abierta

- Mover SL a **break-even** cuando el precio recorra ~1R a favor.
- Considerar **cierre parcial** en 1R y dejar correr el resto con trailing.
- No cerrar por miedo antes del TP ni por euforia mover el TP sin razón técnica.
- Si el motivo por el que entraste desaparece → **sal aunque no toque SL**.

---

## 9. Reglas psicológicas y de disciplina

- Una operación perdedora que siguió el plan es una **buena** operación.
- Una ganadora que rompió el plan es una **mala** operación (mala costumbre).
- Tras alcanzar el límite de pérdida diaria → **apagar la plataforma.**
- Nada de "revancha" (revenge trading) ni operar por aburrimiento o FOMO.
- No operar cansado, enojado o sin haber revisado el calendario económico.

---

## 10. Rutina diaria

**Antes de operar (pre-mercado):**
- [ ] Revisar calendario económico (noticias de alto impacto).
- [ ] Marcar niveles clave en H4/H1/M15 (soportes, resistencias, máx/mín del día previo).
- [ ] Definir sesgo del día: alcista / bajista / neutral.
- [ ] Revisar DXY y contexto general.

**Durante la operación:**
- [ ] Esperar a que el precio llegue a MIS zonas (no perseguir el precio).
- [ ] Confirmar confluencias del setup antes de entrar.
- [ ] Calcular lotaje según riesgo ANTES de abrir.
- [ ] Colocar SL y TP en el momento de entrar.

**Después de operar (post-mercado):**
- [ ] Registrar la operación en el journal (sección 11).
- [ ] Capturar el gráfico (entrada, SL, TP, salida).
- [ ] Anotar el estado emocional y si seguiste el plan.

---

## 11. Journal (registro de operaciones)

Registrar TODO es lo que te hace mejorar. Plantilla:

| Fecha | Sesión | Dirección | Setup | Entrada | SL | TP | R:R | Resultado (R) | ¿Seguí el plan? | Notas |
|---|---|---|---|---|---|---|---|---|---|---|
| | | Compra/Venta | | | | | | +/- | Sí/No | |

Métricas a revisar cada semana/mes:
- **Win rate** (% de aciertos)
- **R promedio** por operación (más importante que el win rate)
- **Expectativa** = (WinRate × R_gano) − (LossRate × R_pierdo)
- % de operaciones donde **respetaste el plan**

---

## 12. Checklist rápido antes de CADA entrada

- [ ] ¿Estoy a favor de la tendencia del marco superior?
- [ ] ¿El precio está en una de MIS zonas marcadas?
- [ ] ¿Tengo al menos 2 confluencias?
- [ ] ¿Hay una vela de confirmación?
- [ ] ¿No hay noticias de alto impacto en los próximos minutos?
- [ ] ¿Calculé el lotaje para arriesgar máx. 1 %?
- [ ] ¿SL y TP definidos con R:R ≥ 1:1.5?
- [ ] ¿No he superado mi límite de pérdida diaria?

**Si alguna respuesta es NO → no hay operación.**

---

## 13. Próximos pasos para desarrollar tu indicador

Como el repo se llama *Indicador-XAUUSD*, un buen siguiente paso es **codificar
las reglas de este plan** en un indicador/alerta:

1. Elige la plataforma: **Pine Script (TradingView)** o **MQL5 (MetaTrader 5)**.
2. Empieza por lo simple: marcar automáticamente niveles clave y sesión de Londres/NY.
3. Añade la lógica de tu setup (p. ej. tendencia + zona + vela de confirmación).
4. Genera **alertas**, no entradas automáticas, hasta validarlo en demo.
5. Haz **backtesting** con datos históricos antes de confiar en él.

> Dime en qué plataforma quieres el indicador y te ayudo a programar la primera versión.
