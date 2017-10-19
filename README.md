# Chimera Code Style
**En esta mini-guía se detallan los puntos básicos a tener en cuenta al momento de escribir código en c# o c++ (ejemplo en c# pero aplicables a ambos) en cualquier proyecto usando Unreal Engine o Unity 3D en Chimera Digital, el objetivo de esta guía es unificar el estilo al escribir código y hacerlo más legible para todo el equipo de programación.**

# Tabulación 
Siempre usar tabulaciones (tabs, equivalen a 4 espacios) para identar el código con espacios iguales, nunca usar múltiples espacios simples para identar.
Ejemplo: 
```csharp
if (value) { 
  //Identado 
  if (value) { 
    //Identado X2 
  } 
}
```

# Espacio entre paréntesis
Mantener un espacio simple entre el contenido de paréntesis entre operadores. 

**Esribir** `(y * x + (n)) ` **en lugar de** ` (y*x+(n)) `

# Llaves 
Siempre usar llaves en funciones, definiciones etc.  para evitar la mas mínima confusión evitar omitir las llaves en aquellos casos que sea posible como en las condiciones. 

**Escribir** `if (value) { //DO }` **en lugar de** `if (value) //DO `
 
# Nombres
Las funciones, clases y encapsulados siempre se nombran iniciando con mayúscula y las variables con minúscula. 
**Ejemplo:**
```csharp
class MyClass { //Clase inicia con mayúscula
  int myInt = 0; //Variable inicia con minúscula
  function MyFunction(int _param){ //Método inicia con mayúscula
    var _someData = 0; //usar guion bajo para variables locales y parámetros 
    //DO 
  } 
}
```
En el caso de Unity 3D, para las variables que referencien componentes usaremos un prefijo con el nombre del componente antes de la variable separado por guion bajo (evitar el guion bajo salvo en este tipo de excepciones). Esto con el fin de facilitar su lectura en el inspector.
**Ejemplo**
```csharp
class MyClass { 
  Transform transform_target = 0; //Variable que referencia un componente de tipo Transform
  Text text_nameHolder = 0; //Variable que referencia un componente de tipo Text
  Animator animator_hairAnimator = 0; //Variable que referencia un componente de tipo Animator
}
```

También deben ser muy claros los nombres que le damos a las variables y métodos, que presenten su contenido y función respectivamente para no dar lugar a malinterpretación y sea más fácil de entender..
**Escribir**
```csharp
class ZombieEnemyBehaviour { //Clase que va a definir el comportamiento de un personaje
  int lifeCount = 3; //Contador de vidas
  float runSpeed = 10; //Velocidad de carrera (correr)
  function Shoot( ){ //Simplemente disparar
    //DO 
  } 
}
```
**En lugar de**
```csharp
class Enemy2 { //Evitar nombres ambiguos
  int l = 3; //Evitar nombres ambiguos
  float s = 10; //Evitar nombres ambiguos
  function Sh( ){ //Evitar nombres ambiguos
    //DO 
  } 
}
```
*Hay que destacar que las variables las nombramos con **sustantivos** y los métodos con **verbos** que describan el resultado a lograr o el retorno esperado si aplica.*


# CamelCase
Al nombrar cualquier clase, objeto o función se debe usar la convención 'CamelCase' donde separamos las palabras con mayúsculas. Las variables las iniciamos con minúscula mientras que clases y funciones con mayúscula.

**Escribir** `int myIntVariable` **en lugar de** `int myintvariable` 
**y escribir** `void ResetLifeCounter()` **en lugar de** `void resetlifecounter()` **o** `void resetLifeCounter()`

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

# Comentarios
Los comentarios son especialmente útiles en funciones con parámetros y/o con retorno. Es importante especificar el fin o contenido esperado en cada parámetro y en el caso de las funciones con retorno especificar qué podemos esperar al retorno.
```csharp
/// <summary>
///  Reduce health value applying damage
/// </summary>
/// <param name="_damage">Amount of health points to remove</param>
void ApplyDamage(float _damage)
{
  helath -+ _damage;
}

/// <returns>Returns a Int value with the age of the player</returns>
int GetPlayerAge()
{
  return myAge;
}
```

## Adicional a alas reglas aquí mencionadas en el caso de Unreal Engine también es importante tener en cuenta el estándar de programación oficial de Unreal [Unreal Engine Coding Standard](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard/)
