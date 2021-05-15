# Taller Web Performance - Midudev

[Slides](https://slides.com/joanleon/taller-de-web-performance-05-2021?token=kzexINcS)

## Chapter 01

- Cada vez las webs estan pesando más.

  - `sudo tcpdump -i en0` --> para ver el trafico de nuestra red en terminal.

- [Objeto PerformanceOberserver en JS](https://developer.mozilla.org/en-US/docs/Web/API/PerformanceObserver)

  - [PerformanceObserverEntryList](https://developer.mozilla.org/en-US/docs/Web/API/PerformanceObserverEntryList)

- [Documentatión de métricas en web.dev](https://web.dev/vitals/)

  - No obsesionarse con el TTI (*Time To Interactive*), pueder ser engañoso. Ya que no mide  que la web sea usable, si no cuando se ejecuta el último task que dura mas de 50ms (a.k.a Long Tasks) en una <u>ventana de 5 segs</u>.. 

    **Consejo:** se pueden cargar esos <u>Long-tasks</u> fuera del Main Thread en un ServiceWorker, y así al no correr en el hilo principal no se considerarán como Long Tasks y no afectarán al TTI.

- [LightHouse Calculator](https://googlechrome.github.io/lighthouse/scorecalc/) --> ver como afecta el cambio de las metricas a la puntuación

- Los [Core Web Vitals](https://web.dev/vitals/) <u>afectan al posicionamiento</u> de las páginas (SEO)

### Monitorización

- Conviene <u>monitorizar la performance de la competencia</u>:
  - Un OKR bueno es llegar a tener un 20% score mejor que la competencia.
- El añadir/quitar features seguramente cambiará el score, por lo que conviene no perderla de vista. 
- Mejor usar una <u>herramienta (e.g [DebugBear](https://www.debugbear.com/)) que use un LightHouse "remoto"</u>, en vez de usarlo en nuestro local. Ya que en local se verá afectado por nuestro SO, red, extensiones, etc.
  - Tambien, usar las mismas herramientas y  metricas en las mediciones, tener en cuenta la geolocalización,...
  - Depurando tu rama local, puede ser complicado usar un servicio externo. Un workaround puede ser correr <u>varias pruebas para ver qué aspecto se puede mejorar</u>.



# Chapter 2



