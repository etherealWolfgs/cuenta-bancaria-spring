# Cajero automático — Spring Core e inyección de dependencias

**Autor:** Genaro Salvador Morales Paoli

## Cómo correrlo

    ./correr.sh App final-app
    ./probar.sh final

## Las piezas

| Bean | Clase | Cómo lo declara Spring (`@Component` o `@Bean`) | Singleton o prototype |
|---|---|---|---|
| cajeroAutomatico | CajeroAutomatico | … | … |
| … | … | … | … |

## Boleto de salida

1. ¿Qué es la inyección de dependencias? Explícalo con el cajero, en tus palabras.
    Con la inyección de dependencias el cajero solo declara que necesita para funcionar, generalmente con interfaces. Spring actua como un ensablador que crea cada componente en memoria y se los inyecta al cajero en el momento de iniciarse. Si esto no sucediera, el tendria que instanciar internamente cada una de sus herramientas mediante el operador new dejandolo fuertemente acoplado, siendo bastante dificil hacer pruebas con él o querer modificar algún componente por cambio de proveedor de antifraude o algún otro proveedor de algun otro componente. 

2. En la MP-1, ¿quién decidía qué antifraude usaba el cajero? ¿Y desde la MP-2?
    El AppSinSpring.java (o lo que debería de ser el cajero como tal) creaba directamente sus dependencias usando el operador new y decidia e instanciaba de forma foja que clase concreta usar. A partir de la MP-2 es Spring quien decide, el programa solo pude o declara que necesita una interface o contrato 

3. ¿Cuándo usarías `@Bean` en vez de `@Component`? Da el ejemplo de hoy.
    Solo podemos usar @Component en clases que programamos nosostros mismos, no en clases de Java como por ejemplo el clock. Para el caso de clock, que es una clase propia de Java, usamos @Bean y se coloca justo encima del método que se va a instanciar (No se puede editar la clase). 
4. ¿Qué gana: `@Primary` o `@Qualifier`? ¿Por qué tiene sentido?
    Tiene prioridad el @Qualifier, ya que @Primary solo marca un Bean por defecto, mientras que @Qualifier inyecta un Bean indicando su nombre, lo cual lo hace mas exacto y con mayor prioridad.
5. En tu proyecto de Empleados de la Semana 3 nunca escribiste `@ComponentScan`. ¿Quién lo hace? (Pista: abre la anotación `@SpringBootApplication` con `Ctrl+clic` y busca las anotaciones que tiene arriba.)

    Es el mismo `@SpringBootApplication`, ya que esta anotación es una anotación compuesta. Eso quiere decir que en su código fuente ya tiene integrado el @ComponentScan, además de @EnableAutoConfiguration y @SpringBootConfiguration. Ejecutando estas anotaciones en automático por detrás.



   Los ejericcios de simulación de module ya se encuentran en la carperta Simuladores_ejercicios!
