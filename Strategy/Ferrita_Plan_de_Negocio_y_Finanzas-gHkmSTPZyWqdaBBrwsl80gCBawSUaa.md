# Ferrita · Plan de negocio, finanzas y cobro

*Versión 1 · 15 de septiembre de 2026 · Para revisar con tu socio.*
*Todos los números salen del archivo `Ferrita_Modelo_Financiero.xlsx`. Si cambiáis un supuesto allí, estos números cambian.*

---

## Resumen en una página

**Qué vendemos.** Preparamos a fabricantes de dispositivos conectados para cumplir el Reglamento de Ciberresiliencia (CRA): inventario de lo que lleva su firmware, qué vulnerabilidades importan de verdad, vigilancia continua y la documentación que pedirá el auditor.

**A quién.** Fabricantes de producto propio con firmware, de 15 a 150 empleados, en Catalunya y el resto de España.

**De dónde sale el dinero.** Cinco productos. Los proyectos de entrada (diagnóstico, triage, paquete CE) traen el cliente; la cuota mensual es lo que convierte esto en empresa.

**Cuánto necesitamos.** Unos 3.400 € de inversión inicial y unos 1.150 €/mes de gastos fijos, más las cuotas de autónomo. Con 20.000 € de capital de los socios hay de sobra: **la empresa no se queda sin caja ni en el escenario pesimista**.

**Qué facturaríamos.**

| Escenario | Año 1 | Año 2 | Clientes de cuota a 24 meses |
|---|---|---|---|
| Pesimista (la mitad de ventas) | ~102.000 € | ~223.000 € | ~7 |
| **Base** | **~205.000 €** | **~446.000 €** | **~14** |
| Optimista | ~287.000 € | ~625.000 € | ~20 |

**El número que importa.** Con **4 clientes de cuota** la empresa paga 2.500 €/mes a cada socio sin depender de vender proyectos. Con **6**, además paga un empleado.

**El riesgo real no es la caja de la empresa.** Es vuestra caja personal los primeros seis meses (en el plan cobráis 0 €) y que el ritmo de ventas del plan base, que es ambicioso, se cumpla. Por eso los criterios de parada siguen siendo los mismos: 3 clientes de pago antes del 31 de diciembre, 4 cuotas antes del 31 de marzo.

---

# 1. Análisis de mercado

## 1.1 El tamaño del problema, con los números oficiales

La propia Comisión Europea, en la evaluación de impacto del CRA, calculó cuánto le va a costar esta ley a las empresas. Esos números son la mejor base que existe para dimensionar el mercado:

- Coste total estimado para la industria: **29.000 millones de euros**.
- Fabricantes y productos afectados: **615.272**.
- Dividido: **unos 47.000 € de coste medio por fabricante**.
- El **99,58 %** de las empresas de este mercado son pymes.
- Coste por producto que estima la Comisión: **unos 42.700 € de desarrollo seguro y 18.400 € de evaluación**. Y es igual para una empresa de 8 personas que para una de 8.000, lo que golpea mucho más a la pequeña.

*(Fuente: evaluación de impacto de la Comisión, recogida en el análisis de Venvera, agosto 2026.)*

**Qué significa para nosotros:** cada fabricante de nuestro perfil tiene por delante un gasto de unos 47.000 € que no sabe cómo hacer. Nuestro paquete completo para un cliente típico (diagnóstico + triage + un año de cuota) son unos 33.500 €. Estamos por debajo de lo que la Comisión considera el coste normal, y le quitamos el problema entero.

Otra referencia útil: un análisis del sector publicado este verano estima que hacerlo a mano, sin herramientas ni experiencia, le lleva a una pyme **entre 25 y 45 días-persona para el primer producto**. *(PortaRegulus, julio 2026.)* A la tarifa media de un freelance de ciberseguridad en España (unos 324 €/día según Malt), eso son **8.000–15.000 € solo en horas**, y sin garantía de hacerlo bien. Nuestro diagnóstico + triage cuesta 9.500 € y lo hace alguien que ya sabe.

## 1.2 Nuestro mercado concreto

| Nivel | Qué es | Estimación | Cómo se calcula |
|---|---|---|---|
| **Mercado total (España)** | Todos los fabricantes españoles de producto conectado con firmware propio, 10–200 empleados | 800–1.500 empresas | Filtro CNAE 26, 27, 28, 32.5 en SABI + clústeres. **Verificadlo con SABI: es la estimación más débil del plan** |
| Gasto total de ese mercado en CRA | 1.000 empresas × 47.000 € | ~47 M€ en 2025–2028 | Coste medio de la Comisión |
| **Mercado alcanzable** | La parte que se externaliza (no lo hacen en casa) | ~40 % → ~19 M€ | Estimación: la mayoría de pymes sin equipo de seguridad no puede hacerlo sola |
| **Nuestro objetivo a 24 meses** | ~25 clientes (14 de cuota) | ~650.000 € acumulados | Plan base del modelo |

Es decir: **aspiramos a menos del 4 % del mercado alcanzable en España**, sin contar el resto de Europa. El tamaño del mercado no es el problema. El problema es la velocidad a la que dos personas pueden vender y entregar.

## 1.3 La competencia, y un hallazgo que cambia el discurso

| Competidor | Qué hace | Precio | Nuestra diferencia |
|---|---|---|---|
| **Escáneres gratuitos** (Grype, Trivy, cve-check de Yocto) | Generan la lista de vulnerabilidades | 0 € | No deciden qué importa ni documentan nada |
| **Timesys Vigiles** | Herramienta para Yocto/Buildroot: SBOM, vigilancia y filtrado por configuración | Plan gratuito + planes de pago | Ver abajo |
| **Plataformas grandes** (Finite State, Cybellum, ONEKEY, Black Duck) | Análisis de firmware para grandes fabricantes | Decenas de miles €/año | No venden a pymes de 40 personas; no se sientan con el ingeniero |
| **Consultoras de ciberseguridad generalistas** | Auditorías, pentesting, ISO 27001 | ~324 €/día freelance, más en consultora | No saben de Yocto ni de firmware |
| **Laboratorios de certificación** | Evalúan y certifican | Por proyecto | No preparan al cliente. **Son partners, no competencia** |

**El hallazgo importante:** Vigiles ya afirma que su filtrado por configuración elimina alrededor del **85 % de los falsos positivos**, y tiene un plan gratuito. Es decir, **"quitamos el ruido del escáner" ya no es un diferenciador por sí solo**: hay una herramienta que hace buena parte de eso gratis.

Esto refuerza lo que ya habíamos hablado: lo que vendemos no es el filtro, es **todo lo que viene después del filtro**, que ninguna herramienta hace:

1. Decidir, con criterio de ingeniero, qué hacer con el 15 % que queda.
2. Justificar por escrito cada decisión de forma que aguante una auditoría.
3. Arreglarlo dentro de su build.
4. Montarle el proceso completo que exige la ley: clasificación, notificación en 24 h, documentación técnica, política de divulgación.
5. Estar ahí cuando sale una vulnerabilidad explotada un viernes a las 7 de la tarde.

De hecho, **Vigiles puede ser una herramienta nuestra**, no un rival. Si el cliente ya lo usa, mejor: le vendemos la capa humana y el cumplimiento encima.

## 1.4 Por qué el precio se sostiene: la comparación que hará el cliente

El cliente va a comparar con **contratar a alguien**. Estos son los números reales de 2026 en España:

- Ingeniero de ciberseguridad, media nacional: **~37.000 € brutos**; en grandes ciudades, **38.500–48.600 €**.
- Con Seguridad Social a cargo de la empresa (~32 %): **~50.000–64.000 € al año**, o **4.200–5.300 €/mes**.
- Y eso sin especialización en embebido, que es más escasa y más cara.

*(Fuentes: Indeed, PageGroup, DKS, agosto 2026.)*

Nuestra cuota de **2.000 €/mes son 24.000 €/año: menos de la mitad de un contratado**, sin vacaciones, sin bajas, sin el riesgo de que se vaya, y con experiencia en muchos clientes en vez de en uno.

**Corrección al documento de tu colega:** él decía que un ingeniero de seguridad embebida cuesta 60.000–75.000 € "totalmente cargado". Es correcto para un perfil sénior en Barcelona, pero la media del mercado está más abajo. Usad **"entre 50.000 y 65.000 € al año con costes"** en las conversaciones: es defendible con datos públicos y sigue siendo más del doble que nosotros.

---

# 2. Modelo de ingresos: de dónde sale el dinero

## 2.1 Los cinco productos

| Producto | Precio | Qué incluye | Horas nuestras | Margen directo* | Papel en el negocio |
|---|---|---|---|---|---|
| **Diagnóstico CRA** | 6.000 € | Clasificación del producto, análisis de qué falta frente a la ley, plan hasta dic-2027, taller con dirección | 40 h | ~79 % | Puerta de entrada. Se vende al director general |
| **Triage de imagen** | 3.500 € / imagen | SBOM real, vulnerabilidades priorizadas, análisis de exposición, justificación para VEX, plan de arreglo | 24 h | ~78 % | Sale del diagnóstico |
| **Cuota de vigilancia** | 2.000 € / mes / producto | Vigilancia diaria, triage de novedades en 48 h, VEX al día, apoyo a la notificación de 24 h, 4 h de ingeniería, reunión mensual | 11 h/mes | ~82 % | **El negocio.** Ingreso recurrente |
| **Ingeniería extra** | 130 €/h (bolsa de 10 h: 1.200 €) | Actualizar capas, backports, cambios en el build | — | Alto | Sale solo de los clientes de cuota |
| **Paquete CE Ready** | 20.000 € / producto | Todo lo anterior + documentación técnica del Anexo VII + acompañamiento en la evaluación con el laboratorio | 140 h | ~77 % | El proyecto grande de 2027 |

*\*Margen directo = precio menos el coste de las horas de un ingeniero contratado (~32 €/h con Seguridad Social). No incluye gastos fijos ni sueldos de los socios.*

## 2.2 Por qué estos precios y no otros

**Diagnóstico a 6.000 € y no más barato.** Es el 13 % de lo que la Comisión estima que le costará el CRA a ese fabricante, y le da el mapa completo de ese gasto. Si lo vendemos a 2.000 €, el director general lo percibe como un informe; a 6.000 €, como un proyecto serio. Rango de negociación: 5.000–8.000 € según el número de productos.

**Triage a 3.500 € por imagen.** Cobrar por imagen, no por empresa, es clave: una empresa con tres productos da tres veces más trabajo. Y el precio está por debajo de lo que les costaría hacerlo a mano (25–45 días-persona).

**Cuota a 2.000 €/mes por producto.** Por encima de lo que proponía tu colega (1.200–1.800 €), porque sus 3 horas incluidas eran irreales: el trabajo de verdad son unas 11 h/mes por cliente. A 2.000 € sale a unos 180 €/hora de nuestro tiempo, que es lo que permite pagar sueldos y crecer. Descuento por volumen: 2–3 productos a 1.700 € cada uno, 4 o más a 1.500 €.

**Paquete CE a 20.000 €.** La Comisión calcula ~61.000 € por producto entre desarrollo seguro y evaluación. Nosotros cubrimos la preparación, no la evaluación del laboratorio ni el rediseño de hardware. Rango 15.000–30.000 € según si el producto es "importante" (necesita laboratorio) o no.

## 2.3 El recorrido de un cliente y lo que vale

1. Firma un **diagnóstico**: 6.000 €.
2. Del diagnóstico sale un **triage** de su producto principal: 3.500 €.
3. Pasa a **cuota**: 2.000 €/mes.
4. Alguna vez pide **horas extra**: ~1,5 h/mes de media.
5. Si su producto es "importante", en 2027 contrata el **paquete CE**: 20.000 €.

**Valor de un cliente típico en 3 años (sin paquete CE): ~88.500 €.** Con paquete CE, ~108.500 €.

Esto responde a la pregunta "¿cuánto podemos gastar en conseguir un cliente?": con una regla prudente de no gastar más de una quinta parte de lo que vale, **hasta ~17.700 € por cliente**. En la práctica significa que un desayuno técnico de 400 €, una cuota de clúster de 600 € o un mes de Sales Navigator de 90 € están regalados si traen un solo cliente.

## 2.4 Cómo evoluciona la mezcla de ingresos

| | Año 1 | Año 2 |
|---|---|---|
| Proyectos (diagnóstico + triage + CE) | ~61 % | ~30 % |
| Recurrentes (cuota + horas extra) | ~39 % | ~70 % |

El primer año vivís de proyectos, que son irregulares. El segundo, de cuotas, que son estables. **Esa transición es el objetivo estratégico de todo el plan**: una empresa de proyectos vale poco y agota; una de cuotas es sostenible y, si algún día queréis, vendible.

---

# 3. Planes de cobro: cómo cobramos exactamente

Decidirlo antes de la primera propuesta evita negociar condiciones distintas con cada cliente.

## 3.1 Condiciones por producto

| Producto | Cuándo se cobra | Forma de pago | Por qué así |
|---|---|---|---|
| **Diagnóstico** | 50 % al firmar, 50 % a la entrega | Transferencia a 15 días | El 50 % inicial filtra a quien no va en serio y financia el trabajo |
| **Triage** | 50 % al firmar, 50 % a la entrega | Transferencia a 15 días | Igual |
| **Cuota** | Mensual, por adelantado, el día 1 | Domiciliación SEPA (GoCardless, ~1 % + 0,20 €) o transferencia | Domiciliado = cero persecución de impagos |
| **Cuota, pago anual** | 12 meses por adelantado con **10 % de descuento** | Transferencia | Os da caja de golpe; al cliente le ahorra 2.400 € |
| **Horas extra** | A mes vencido, o bolsa de 10 h prepagada (1.200 €) | Transferencia | La bolsa prepagada es mejor para vosotros: cobráis antes y el cliente ahorra 100 € |
| **Paquete CE** | 40 % al inicio, 30 % a mitad, 30 % a la entrega | Transferencia a 15 días | Proyecto largo: nunca adelantéis más de un tercio de trabajo sin cobrar |

## 3.2 Condiciones del contrato de cuota

- **Compromiso mínimo de 12 meses.** La ley obliga a vigilar durante toda la vida del producto; un contrato mes a mes no tiene sentido para el cliente y os deja expuestos a vosotros.
- **Renovación automática anual**, con cancelación avisando 60 días antes.
- **Revisión de precio anual** ligada al IPC, como máximo.
- **Qué pasa si el cliente pide mucho más de lo incluido:** las horas por encima de las 4 incluidas se facturan a 130 €/h, avisando antes. Esto tiene que estar escrito o acabaréis regalando horas.
- **Impago:** a los 30 días se suspende la vigilancia (y se le avisa por escrito de que deja de estar cubierto frente a la notificación de 24 h). Es una palanca fuerte.

## 3.3 Precio de lanzamiento (en vez de la auditoría gratis)

Para los **5 primeros clientes**: **25 % de descuento en el diagnóstico** (4.500 € en vez de 6.000 €) a cambio de:
1. Poder usar su nombre como referencia.
2. Un caso de estudio anonimizado.
3. Una reunión de 30 minutos de feedback al terminar.

Esto os da referencias sin regalar el trabajo ni destruir el precio.

## 3.4 Aspectos fiscales y de facturación

- **IVA:** todos los precios son **sin IVA**. A clientes españoles se factura con 21 % de IVA. A empresas de otros países de la UE con NIF intracomunitario, sin IVA (inversión del sujeto pasivo). Vuestra gestoría lo lleva.
- **Software de facturación:** usad **Holded, Quipu o el que os recomiende la gestoría**, no un Word. El sistema VeriFactu obligará a las sociedades a facturar con software homologado; según el calendario actual entra en 2027. Confirmad la fecha exacta con la gestoría y empezad ya con uno que lo cumpla.
- **Impuesto de sociedades:** con el certificado de **empresa emergente** (Ley 28/2022), 15 % en lugar de 25 % durante los primeros cuatro años con beneficio. Pedidlo al constituir.

---

# 4. Costes e inversión: en qué gastamos

## 4.1 Inversión inicial: ~3.440 €

| Concepto | Importe | ¿Imprescindible? | Por qué |
|---|---|---|---|
| Constitución de la SL | 600 € | Sí | Sin sociedad no hay facturas, ni certificado de startup, ni ENISA |
| Abogado: pacto de socios + contrato marco + cláusula VEX | 1.500 € | Sí | Cubre los dos riesgos más graves: el legal (VEX) y el humano (socios) |
| Registro de marca en OEPM (3 clases) | 350 € | Muy recomendable | Protege "Ferrita" en España. La marca UE (~1.050 €) puede esperar |
| Dominios en Cloudflare | 40 € | Sí | Principal + secundario de envío |
| Laboratorio: placas de desarrollo, depurador, analizador lógico | 800 € | Muy recomendable | Para el informe de ejemplo y para reproducir problemas sin tocar el hardware del cliente |
| Tarjetas e impresos | 150 € | Opcional | Solo para eventos presenciales |
| Web | 0 € | — | HTML en Cloudflare Pages, gratis |

*No incluye ordenadores (se asume que los tenéis).*

## 4.2 Gastos fijos mensuales: ~1.150 €/mes

| Concepto | €/mes | Por qué |
|---|---|---|
| Gestoría | 150 | Obligaciones trimestrales y anuales de la SL |
| Seguro RC profesional + ciber | 167 | El seguro del "dijimos que no afectaba y sí afectaba" |
| Correo (Zoho Free) | 0 | Gratis hasta 5 buzones |
| Instantly (envío y calentamiento) | 35 | Sin esto los emails van a spam |
| LinkedIn Sales Navigator | 90 | Encontrar al interlocutor correcto |
| Servidor para escaneos | 40 | Los datos de clientes no se procesan en un portátil |
| Cuota de clúster | 50 | Directorio, eventos, credibilidad |
| Eventos y marketing | 250 | Un desayuno técnico por trimestre + alguna feria |
| Desplazamientos | 150 | En industrial se cierra en persona |
| Teléfono, banco, formación, software | 115 | |
| Imprevistos (10 %) | ~105 | Siempre aparece algo |

Más **cuotas de autónomo societario: 315 €/mes por socio** (base mínima 1.000 € × 31,4 %). Ojo: en la regularización anual la base mínima de los societarios puede subir a 1.424 €, lo que llevaría la cuota a ~448 €. **Preguntad a la gestoría** si podéis acogeros a la tarifa plana de 80 €: si sí, os ahorráis unos 5.500 € el primer año entre los dos.

## 4.3 Sueldos (retiradas de los socios)

| Periodo | Por socio | Por qué |
|---|---|---|
| Meses 1–6 (oct-26 a mar-27) | **0 €** | Validación. Todo lo que entra se queda en la empresa |
| Meses 7–12 (abr-27 a sep-27) | 1.500 € | Mínimo para vivir, si hay clientes |
| Meses 13–24 | 2.500 € | Sueldo modesto razonable |

**Importante:** el modelo es deliberadamente tacaño en sueldos. En el escenario base la empresa acumula mucha caja a partir del mes 9. Eso no es "beneficio para repartir" hasta que lo decidáis: es **el margen para subiros el sueldo o contratar antes**. Cuando llevéis tres meses seguidos por encima del plan, revisad la retirada al alza.

## 4.4 Primera contratación

- **Cuándo:** al llegar a **5 clientes de cuota**. En el plan base, hacia **agosto de 2027**; en el optimista, junio de 2027; en el pesimista, enero de 2028.
- **Perfil:** ingeniero de sistemas embebidos de nivel medio que sepa Yocto o Buildroot. La seguridad se le enseña; el embebido, no.
- **Coste:** 38.000 € brutos → **~4.180 €/mes** con Seguridad Social.
- **Por qué en ese momento:** con 5 cuotas (~55 h/mes) más los proyectos, dos personas pasan del 100 % de ocupación. Contratar antes no hay caja; después, empezáis a entregar mal.

El modelo tiene una fila de **ocupación**: si pasa del 100 % (se pinta en rojo), estáis vendiendo más de lo que podéis entregar. En el escenario base roza el 100 % justo antes de contratar; en el optimista llega al 140 %: si las ventas van mejor de lo previsto, **contratad antes, no trabajéis 70 horas a la semana**.

---

# 5. Financiación: ¿hace falta dinero de fuera?

## 5.1 Lo que dice el modelo

| Escenario | Caja mínima en 24 meses | ¿Os quedáis sin caja? |
|---|---|---|
| Pesimista | ~14.350 € | No |
| Base | ~14.800 € | No |
| Optimista | ~14.800 € | No |

La caja mínima llega en los primeros dos meses y ya no baja. **Con 20.000 € de capital (10.000 € cada uno) la empresa no necesita financiación externa en ningún escenario.**

La razón es simple: los gastos fijos son muy bajos y los socios no cobran los primeros seis meses. **El coste de este negocio es vuestro tiempo, no dinero.**

## 5.2 Entonces, ¿ENISA sí o no?

**Mi recomendación: no pedirlo de entrada.**

- No hace falta para sobrevivir.
- Os costaría intereses (tramo fijo en torno al Euríbor + 3,25 %, más un tramo variable ligado a beneficios).
- La solicitud lleva tiempo y papeleo en los meses en que tenéis que estar vendiendo.

**Cuándo sí tendría sentido:** si en marzo de 2027 las ventas van por encima del plan y queréis contratar a dos personas a la vez, o subiros el sueldo antes. Entonces un préstamo participativo sin avales y sin ceder participaciones es la mejor opción disponible.

Datos a tener en cuenta cuando llegue el momento: la línea para socios jóvenes (en torno a 40 años o menos) ha llegado hasta 75.000 € con fondos propios de al menos el 50 % del préstamo; las demás líneas exigen fondos propios iguales al préstamo. **Una fuente de septiembre de 2026 indica que ENISA ha reorganizado sus líneas y los nombres antiguos ya no son los vigentes**: comprobad las condiciones actuales directamente en enisa.es antes de contar con ello.

## 5.3 Lo que sí hace falta: vuestro colchón personal

Esta es la cuenta que el modelo no puede hacer por vosotros:

> **Colchón personal mínimo = (vuestros gastos personales al mes × 6) + ((gastos personales − 1.500 €) × 6)**

Ejemplo: si cada uno necesita 2.000 €/mes para vivir, necesitáis 12.000 € para los meses 1–6 más 3.000 € para cubrir la diferencia en los meses 7–12. **15.000 € cada uno, además de los 10.000 € de capital.**

Si alguno no llega, la alternativa sensata es que uno de los dos mantenga un trabajo a media jornada los primeros meses. Hacedlo explícito en el pacto de socios.

---

# 6. Los números del escenario base, trimestre a trimestre

| Trimestre | Clientes de cuota (final) | Facturación | Gastos | Caja final |
|---|---|---|---|---|
| Q4 2026 | 0 | ~9.500 € | ~9.300 € | ~18.500 € |
| Q1 2027 | ~2 | ~34.000 € | ~6.800 € | ~42.000 € |
| Q2 2027 | ~5 | ~62.000 € | ~16.700 € | ~87.000 € |
| Q3 2027 | ~8 | ~99.000 € | ~26.300 € | ~159.000 € |
| Q4 2027 | ~10 | ~123.000 € | ~37.200 € | ~245.000 € |
| 2028 (9 meses) | ~14 | ~323.000 € | ~107.000 € | ~463.000 € |

*Cifras redondeadas; el detalle mes a mes está en la hoja "Modelo 24m". Sin IVA ni impuesto de sociedades.*

**Punto de equilibrio:**

| Para cubrir… | Clientes de cuota necesarios |
|---|---|
| Solo gastos y autónomos (sin sueldos) | 1 |
| + 1.500 €/mes cada socio | 3 |
| **+ 2.500 €/mes cada socio** | **4** |
| + 2.500 €/mes cada socio + 1 empleado | 6 |

---

# 7. Qué puede hacer que estos números no se cumplan

Ordenado por cuánto afecta al modelo:

1. **Que el ritmo de ventas sea más lento.** El plan base supone ~1 diagnóstico al mes desde noviembre. Para dos desconocidos es ambicioso. El escenario pesimista (la mitad) sigue siendo viable, pero con sueldos más bajos durante más tiempo. **Vigilad los criterios de parada.**
2. **Que las horas reales por cliente sean más.** Si la cuota os lleva 20 h/mes en vez de 11, el margen baja a la mitad y la ocupación se dispara. Medidlo desde el primer cliente y cambiad el supuesto en el Excel.
3. **Que la demanda caiga después de diciembre de 2027.** El modelo ya lo asume (menos diagnósticos en 2028), pero si cae más de lo previsto, el negocio depende al 100 % de las cuotas. Por eso son tan importantes.
4. **Que el cliente pague tarde.** El modelo supone que los clientes pagan en plazo. En pymes industriales, 60–90 días es habitual. Con el 50 % por adelantado y la domiciliación se mitiga mucho.
5. **Que las cuotas de autónomo sean más altas.** Diferencia de ~1.600 €/año por socio entre 315 € y 448 €. No cambia la viabilidad.

---

# 8. Decisiones que tenéis que tomar vosotros

Estas celdas del Excel están en amarillo porque dependen de vosotros:

1. **Capital que aporta cada uno.** Provisional: 10.000 € cada uno.
2. **Retirada de cada socio en cada fase.** Provisional: 0 / 1.500 / 2.500 €.
3. **Horas reales del triage**, cuando hagáis el informe de ejemplo.
4. **Escenario con el que planificáis.** Mi recomendación: planificad los gastos con el pesimista y las contrataciones con el base.
