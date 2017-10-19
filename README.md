# Chimera Code Style
**En esta mini-guía se detallan los puntos básicos a tener en cuenta al momento de escribir código en c# o c++ (ejemplo en c# pero aplicables a ambos) en cualquier proyecto usando Unreal Engine o Unity 3D en Chimera Digital, el objetivo de esta guía es unificar el estilo al escribir código y hacerlo más legible para todo el equipo de programación.**

# Tabulación 
Siempre usar tabulaciones (tabs, equivalen a 4 espacios) para identar el código con espacios iguales, nunca usar múltiples espacios simples para identar.
Ejemplo: 
```csharp
if ( value ) { 
  //Identado 
  if ( value ) { 
    //Identado X2 
  } 
}
```

# Espacio entre paréntesis
Mantener un espacio simple entre el contenido de paréntesis entre operadores. 

**Esribir** ` ( y * x + ( n ) ) ` **en lugar de** ` (y*x+(n)) `

# Llaves 
Siempre usar llaves en funciones, definiciones etc.  para evitar la mas mínima confusión evitar omitir las llaves en aquellos casos que sea posible como en las condiciones. 

**Escribir ** `if ( value ) { //DO }` **en lugar de** `if ( value ) //DO `
 
# Prefijos
Usar prefijos para diferenciar de manera mas simple el origen y contexto de las variables, por ejemplo `m_miEntero = 0;` **en lugar de** `miEntero = 0;`
* m_ para variables globales o miembros de la clase
* s_ para variables estáticas
* c_ para constantes
* e_ para eventos
* _ guion bajo solo para variables locales de funciones/métodos
 
# Nombres
Las funciones, clases y encapsulados siempre se nombran iniciando con mayúscula y las variables con minúscula. 
**Ejemplo:**
```csharp
class MyClass { //Clase inicia con mayúscula
  int m_myInt = 0; //Variable inicia con minúscula
  function MyFunction( ){ //Método inicia con mayúscula
    //DO 
  } 
}
```
También deben ser muy claros los nombres que le damos a las variables y métodos, que presenten su contenido y función respectivamente para no dar lugar a malinterpretación y sea más fácil de entender..
**Escribir**
```csharp
class ZombieEnemyBehaviour { //Clase que va a definir el comportamiento de un personaje
  int m_lifeCount = 3; //Contador de vidas
  float m_runSpeed = 10; //Velocidad de carrera (correr)
  function Shoot( ){ //Simplemente disparar
    //DO 
  } 
}
```
**En lugar de**
```csharp
class Enemy2 { //Evitar nombres ambiguos
  int m_l = 3; //Evitar nombres ambiguos
  float m_s = 10; //Evitar nombres ambiguos
  function Sh( ){ //Evitar nombres ambiguos
    //DO 
  } 
}
```
*Hay que destacar que las variables las nombramos con **sustantivos** y los métodos con **verbos** que describan el resultado a lograr o el retorno esperado si aplica.*


# CamelCase
Al nombrar cualquier clase, objeto o función se debe usar la convención 'CamelCase' donde separamos las palabras con mayúsculas. 

**Escribir** `int _miVariableEntera` **en lugar de** `int _mivariablenetera`

# Sobrecarga 
Evitar la sobrecarga de métodos/funciones tanto como sea posible, siempre crear métodos con objetivos muy específicos y que sea claro cuál es su función con solo leer el nombre. 

**Escribir**
```csharp
void Shoot()
{
  //DO
}

void ShootIgnoringLayer( int _layer )
{
  //DO
}
```
**En lugar de**
```csharp
void Shoot()
{
  //DO
}

void Shoot( int _layer )
{
  //DO
}
```
 
 # Inicialización 
Inicializar variables siempre que sea posible y validar que no sean nulas antes de realizar cualquier operación. Al verificar si una variable es nula hacerlo de manera literal. **Escribir** `if ( MyType != null )` en lugar de `if ( MyType )`
```csharp
MyType* m_objectA = nullptr; //c++
MyType m_objectB = null;
void DoSomething()
{
/*****************Pointers************************/
  if ( m_objectA != nullptr )
  {
    //DO
  }
  else
  {
    Log("Null reference...")
  }
/*****************Variables********************/
  if ( m_objectB != null )
  {
    //DO
  }
  else
  {
    Log("Null reference...")
  }
}
```

## Adicional a alas reglas aquí mencionadas en el caso de Unreal Engine también es importante tener en cuenta el estándar de programación oficial de Unreal [Unreal Engine Coding Standard](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard/)
