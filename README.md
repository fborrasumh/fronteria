# FronterIA

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23003243.svg)](https://doi.org/10.5281/zenodo.23003243)

**Aplicación:** https://fborrasumh.github.io/fronteria/ · Español, English, Português

**De tu pregunta de investigación a una propuesta revisada.** Escribes qué quieres investigar, en cualquier disciplina, y un equipo de agentes de IA hace el ciclo del marco **ScientistTwo** (Nam et al., 2026, arXiv:2609.19644):

1. identifica las limitaciones del estado del arte;
2. propone ideas y contrasta su novedad con las publicaciones más parecidas de **OpenAlex**;
3. diseña un piloto y un estudio completo, empezando por la idea más novedosa. Un crítico metodológico lo puntúa; si no llega a 6/10, reformula la pregunta y dice qué cambiar, y el diseño se rehace (hasta 3 veces por idea). El proceso no se detiene: si ninguna idea se aprueba, sigue con la mejor puntuada «con reservas» y la propuesta declara las objeciones;
4. planifica las ablaciones;
5. redacta la propuesta y la somete a un revisor simulado; si la nota es menor que 7, la mejora y la vuelve a revisar.

Tres pasos en pantalla (pregunta → ideas → propuesta), un botón y ningún parámetro que ajustar. Un solo fichero (`index.html`), sin servidor.

> No es una aplicación de los autores de ScientistTwo. La propuesta es un borrador para revisión humana.

## Qué hace la IA y qué comprueba el código

- **La IA propone:** limitaciones, ideas, puntuación de novedad, diseños, críticas, ablaciones, la propuesta y la revisión.
- **El código decide y comprueba:**
  - las publicaciones cercanas vienen de OpenAlex, no de la IA;
  - la aprobación la decide el código con la nota del crítico (6/10 o más), y la idea elegida es la más novedosa de las aprobadas;
  - cada cita de la propuesta, del tipo «(Apellido, año)» o «Apellido (año)», se busca entre esas publicaciones;
  - las citas que no aparecen se marcan con ⚠;
  - la bibliografía la escribe el código solo con las publicaciones encontradas.

## Ejemplo sin clave

«Ver un ejemplo» enseña una investigación completa en los tres idiomas, sin usar la IA. Trata sobre una intervención para mejorar el aprendizaje de Estadística en primer curso.
- Las publicaciones del ejemplo son reales y sus DOI están comprobados, pero se eligieron a mano: no salen de una búsqueda en OpenAlex.
- La propuesta incluye a propósito una cita inexistente, (Smith, 2019), para mostrar cómo la marca el código.

## Privacidad

- Tu pregunta y tus resultados se guardan solo en este navegador (IndexedDB).
- Al investigar, la pregunta sale hacia tu proveedor de IA (OpenAI, Google Gemini o Anthropic Claude) con tu clave.
  - Antes, se enmascaran correos y teléfonos.
  - Antes del primer envío ves una muestra de lo que sale.
- Hacia OpenAlex solo salen búsquedas breves en inglés.
- Cada ejecución hace unas 10-25 consultas a la IA (como máximo, 8 rondas de diseño y crítica).

## Límites

- Un modelo de lenguaje estima la novedad frente a unas pocas publicaciones cercanas. No es una revisión sistemática.
- No se ejecuta ningún experimento: los resultados de la propuesta son esperados.
- El revisor es una IA. Su nota orienta, pero no certifica la calidad.
- Si OpenAlex no responde, la app lo avisa y ninguna cita queda comprobada.

## Novedades de la versión 2.1

- El proceso ya no se detiene cuando el crítico no aprueba un diseño. El crítico reformula la pregunta y dice qué cambiar, el diseño se rehace, y si ninguna idea llega a aprobarse se sigue con la mejor puntuada y la propuesta declara las objeciones pendientes.

## Novedades de la versión 2.0

- Pensada para cualquier investigador: solo modo propuesta, en cualquier disciplina, sin parámetros.
- Se retira el laboratorio ejecutable de aprendizaje automático (Pyodide), que sigue disponible en la versión 1.0.0 archivada en Zenodo.
- Funciona con OpenAI, Gemini y Claude, y está en español, inglés y portugués.
- Las citas de la propuesta se comprueban por código.

## Cómo citar

Borrás Rocher, F. (2026). *FronterIA* (versión 2.1.0) [Software]. Universidad Miguel Hernández de Elche. https://doi.org/10.5281/zenodo.23003243

El DOI es el de concepto: apunta siempre a la última versión. GitHub ofrece la cita en APA y BibTeX con el botón *Cite this repository*, a partir de `CITATION.cff`.

**Referencia del marco:** Nam, J., Yoon, J., Pan, Y., Wang, Y., Meng, R., Ranganathan, P. y Pfister, T. (2026). *ScientistTwo: Pioneering the Human Knowledge Frontier with Autonomous AI*. arXiv:2609.19644.

Forma parte del catálogo [Herramientas IA para la academia](https://fborrasumh.github.io/ia/).

## Licencia

MIT © 2026 Fernando Borrás Rocher · Universidad Miguel Hernández de Elche.
