# **Arquitecturas CSS en apps JS**

# Posibles problemas de arquitectura

Cosas a tener en cuenta.

## Falta de cohesión

Al tener los estilos aislados en cada componente, si no establecemos una forma de trabajar como equipo, cada dev puede aplicar los estilos de una forma distinta, aumentando la carga cognitiva y dificultando la colaboración. **Establecer una forma de trabajar** es importante en cualquier aspecto del desarrollo

## Nomenclatura

Usar una **nomenclatura común** para todos y pensar en **nombres que comuniquen bien su intención.**

## Separación de responsabilidades

**Separar estilos presentacionales de los de layout**. Un componente `<Button/>` será menos reutilizable si maneja márgenes o posicionamiento, que luego puede que no haga falta en algun otro caso.

# Nomenclatura de clases en componentes JS

Aunque los estilos de los componentes estes *scoped* dentro del componente puede ser que las clases no colisionen. Aún así, es interesante **seguir usando BEM** para tener una convención de clases.

# ATOMITCSS en aplicaciones JS

[Demo en Github](https://github.com/CodelyTV/css-architecture-course/tree/main/7-3-vue-app)