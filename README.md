# FronterIA

**Aplicación:** https://fborrasumh.github.io/fronteria/

Un equipo de agentes de IA que **investiga de forma autónoma**. Implementa a escala de navegador el marco **ScientistTwo** (Nam et al., 2026, arXiv:2609.19644). La persona plantea el problema y los agentes hacen el resto:

- identifican las limitaciones del estado del arte;
- generan ideas y contrastan su novedad con trabajos reales de OpenAlex;
- las prueban primero en un subconjunto y luego en el benchmark completo;
- las hacen evolucionar con lo aprendido;
- ejecutan ablaciones;
- redactan el artículo, lo someten a un revisor simulado, responden con experimentos nuevos y pasan una metarrevisión.

Aplicación de un solo fichero (`index.html`), sin servidor, con el diseño de la familia Forja.

> No es una aplicación de los autores de ScientistTwo. Sirve para entender el marco, enseñarlo y explorar ideas; el artículo que genera es un borrador para revisión humana.

## Dos modos

- **Laboratorio ejecutable.** El reto es superar a un clasificador de referencia (un bosque aleatorio) en un benchmark tabular de cinco conjuntos, con F1 macro y exactitud y validación cruzada estratificada. Se puede añadir un CSV propio. Los agentes escriben código de scikit-learn que **se ejecuta de verdad en el navegador** (Pyodide), y el artículo lleva las tablas con esos resultados.
- **Propuesta de investigación.** Para cualquier disciplina, con el mismo ciclo sin ejecución: diseño con piloto y estudio completo, plan de ablaciones y una propuesta revisada que solo cita trabajos encontrados en OpenAlex.

## El ciclo (§3 del artículo)

Cada etapa sigue el mismo patrón: un **candidato**, un **crítico** que acepta, descarta o pide refinar, y un presupuesto de rondas.

| Etapa | Agentes |
|---|---|
| Limitaciones y semillas | Extractor y verificador de limitaciones, generador de ideas, comprobador de novedad (OpenAlex) |
| Subconjunto → completo | Programadores, críticos e ingeniero |
| Evolución y selección | Evolucionador de ideas y selector |
| Ablaciones | Planificador, programador y crítico de ablaciones, comparador de resultados |
| Artículo y revisión | Redactor, revisor (escala ICLR), planificador y programador de la réplica, mejorador del borrador |
| Metarrevisión | Metarrevisor |

## Salvaguardas añadidas

- Un crítico no puede dar por buena una idea que no mejora a la referencia, y lo que queda más de 2 puntos por debajo se descarta.
- El código se revisa antes de ejecutarse: solo se permiten scikit-learn, NumPy y SciPy, sin ficheros ni red.
- Las cifras del artículo se contrastan con los resultados reales, y las que no cuadran se marcan.
- El refinamiento tras las ablaciones solo se adopta si es estrictamente mejor.
- Se exporta un script de Python que reproduce los resultados fuera del navegador.

## Ejemplo sin clave

La app incluye una investigación real ya ejecutada:
- la referencia obtiene un F1 de 0,9163;
- dos ideas se descartan;
- la idea evolucionada (árboles extremos, SVC y logística en voto blando) llega a 0,9242;
- las ablaciones muestran que la mejora la sostienen los árboles y la SVC;
- la réplica descubre que, con un 20 % de etiquetas ruidosas, la referencia es mejor.

## Privacidad

Los experimentos y los datos propios se procesan en el navegador. El texto viaja a OpenAI con la clave del usuario, que se guarda en `localStorage` (`ia_openai_key`), y las búsquedas bibliográficas van a OpenAlex.

## Referencia del marco

Nam, J., Yoon, J., Pan, Y., Wang, Y., Meng, R., Ranganathan, P. y Pfister, T. (2026). *ScientistTwo: Pioneering the Human Knowledge Frontier with Autonomous AI*. arXiv:2609.19644.

Forma parte del catálogo [Herramientas IA para la academia](https://fborrasumh.github.io/ia/).

## Licencia

MIT © 2026 Fernando Borrás Rocher · Universidad Miguel Hernández de Elche.
