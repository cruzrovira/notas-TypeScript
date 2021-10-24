# typeScript

mini resumen de typeScript para poder aprender de manera rapida .

### Primitivos :

boolean,  
number,  
string,  
void, null  
y undefined  
enum : definido por el usuario  
void : indica ausencia de valor

### Tipo de objeto : es todo lo que no es primitivo

1. **Enumerados**

```typescript
enum sexo {
  Masculino = 1,
  Femenino,
}
```

Por defecto los valores comienzan 0 , peor puede cambiar el valor de inicio

2. **Tipos de unión (|)**  
   Indica que el tipo de daros para una variable puede ser más de un tipo permitido  
   let multiType: number | boolean;

3. **Tipo de intercepción (&)**  
   Une varios tipos de daros para formar uno nuevo con los indicados en los elementos anteriores se utiliza más con interfaces .

```typescript
interface persona {
	Nombre :string;
	Edad : number;
}

interface Empelado {
	Puesto :string;
}

type perosnaEmpleado = persona & empeñado;

let Newempelado : personaEmpelado = {
	Nombre :”Oscar”
	Edad: 40,
	Puesto: “gerente”
};
```

### Tipos literales

type testResult = "pass" | "fail" | "incomplete";

Los tipos Lira telas pueden ser de tipo string, number, bolean

### Trices o arreglos

let list: number[] = [1, 2, 3];  
let list: Array<number> = [1, 2, 3];

### Tuplas

let person1: [string, number] = ['Marcia', 35];

### Interfaz

```typescript
interface Persona {
  Nombre: string;
  Apellido: string;
  NombreCompelto(): string;
}
```

### Modo de uso de la interfaz

```typescript
let p:persona = {
  Nombre : "Emil",
  Apellido : "Andersson",
  NombreCompleto(): string {
  return this.nombre+ " " + this.apellido;
  }
}

P.nombre = “Oscar”;

```

### Características de las interfaces

firstName?: string;  
Indica que la propiedad puede ser obsional

redOnly firstName?: string;  
Propiedad de solo lectura

### Herencia al crear interfaces

```typescript
interface Sundae extends IceCream {
  sauce: "chocolate" | "caramel" | "strawberry";
  nuts?: boolean;
  whippedCream?: boolean;
  instructions?: boolean;
}
```

### Creación de tipos indexados

Estos indican el valor de indexación y el tipo que devolverá

```typescript
interface IceCreamArray {
  [index: number]: string;
}

let myIceCream: IceCreamArray;
myIceCream = ["chocolate", "vanilla", "strawberry"];
let myStr: string = myIceCream[0];
console.log(myStr);
```

### api fetch

```typescript
const fetchURL = "https://jsonplaceholder.typicode.com/posts";

interface Post {
  Id: number;
  title: string;
}

async function fetchPosts(url: string) {
  let response = await fetch(url);
  let body = await response.json();
  return body as Post[];
}

async function showPost() {
  let posts = await fetchPosts(fetchURL);
  let post = posts[0];
  console.log("Post #" + post.id);
  console.log("Title: " + post.title);
}

showPost();
```

### Funciones con nombre

```typeScript
function suma (x: number, y: number): number {
   return x + y;
}
suma (1, 2);
```

### Funciones anónimas

importate las funciones anonimas no se elevan , adiferencia de las funciones con nombre , por tanto debe declararlas antes de llamarlas

```typeScript
let suma = function (x: number, y: number): number {
   return x + y;
}
suma(1, 2);
```

### Funciones de flecha `=>`

```typeScript
// Anonymous function
let addNumbers1 = function (x: number, y: number): number {
   return x + y;
}

// Arrow function
let addNumbers2 = (x: number, y: number): number => x + y;
```

### Parámetros obligatorios

```typeScript
function suma (x: number, y: number): number {
   return x + y;
}

suma(1, 2); // Returns 3
suma(1);    // Returns an error
```

### Parámetros opcionales `?`

```typeScript
function suma (x: number, y?: number): number {
   return x + y;
}

suma(1, 2); // Returns 3
suma(1);    // Returns 1
```

### Parámetros predeterminados

los parámetros predeterminados deben aparecer después de los parámetros necesarios en la lista de parámetros.

```typeScript
function suma (x: number, y = 25): number {
   return x + y;
}

suma(1, 2);  // Returns 3
suma(1);     // Returns 26

```

### Parámetros de REST

Los parámetros de REST se tratan como un número sin límite de parámetros opcionales. Puede dejarlos desactivados o tener tantos como desee.

```typeScript
let sumar = (numero: number, ...otros: number[]): number => {
   let total: number = numero;
   for(let counter = 0; counter < otros.length; counter++) {
      if(isNaN(otros[counter])){
         continue;
      }
      total += Number(otros[counter]);
   }
   return total;
}
// llamadas a funcion
sumar(1, 2, 3, 4, 5, 6, 7);  // returns 28
sumar(2);                    // returns 2
sumar(2, 3, "three");        // flags error due to data type at design time, returns 5
```

### Parámetros de objeto desconstruido

Los parámetros de función son posicionales y deben pasarse en el orden en el que se definen en la función.

```typeScript
interface Message {
   text: string;
   sender: string;
}

function displayMessage({text, sender}: Message) {
    console.log(`Message from ${sender}: ${text}`);
}

displayMessage({sender: 'Christopher', text: 'hello, world'});
```

### Creación de una clase

```typeScript
class Auto {
    // Properties
      _marca:string;
      _modelo:string;
      _puertas:number;

    // Constructor
    constructor(marca:string, modelo:string , puertas:number =4){
      this._marca= marca;
      this._modelo= modelo;
      this._puertas= puerts;

    }
    // Accessors
   get marca():string{
      return this._marca;
    }
    set set(marca:string):void {
        this._marca = marca;
    }
    // Methods
    worker(): string {
    return this._make;
}

}
```

### Creacion de instancia de una clase

```typeScript
let Car1 = new Auto('toyota', 'ailux', 4);
console.log(Car1.marca)
```

### modificadores de acceso

De forma predeterminada, todos los miembros de clase son de tipo public.

- public
- privae
- protected

## propiedades estáticas

odas las instancias de una clase comparten las propiedades y los métodos estáticos.
Tenga en cuenta que se usa la sintaxis `className.propertyName` en lugar de `this.` cuando se obtiene acceso a la propiedad estática.

```typeScript
class Auto {
   // Properties
   static _nautos :number =1;
     _marca:string;
     _modelo:string;
     _puertas:number;

   // Constructor
   constructor(marca:string, modelo:string , puertas:number =4){
     this._marca= marca;
     this._modelo= modelo;
     this._puertas= puerts;
     Auto._nautos++;
   }
   // Accessors
  get marca():string{
     return this._marca;
   }
   set set(marca:string):void {
       this._marca = marca;
   }
   //static
   static getNautos():number{
      return Auto._nautos;
   }

   // Methods
   worker(): string {
   return this._make;
   }

}
// importante para utilizar los staticos
// no es necesario realizar la instancia de la clase
console.log(Auto.getNautos());
```

### herencia

```typeScript
class autoElectrico extends Auto {
    // Properties unique to ElectricCar
   private _range: number;
    // Constructor
  constructor(range:number,marca:string, modelo:string , puertas:number =4){
     super(marca,modelo,puertas)
     this._range=range;
   }
    // Accessors

    // Methods

}
```

### interfaz para asegurar la forma de la clase

es importante destacar que las interfases solo indican las propiedades y fucniones publicas

```typeScript
interface vehiculo {
    marca: string;
    modelo: string;
    puertas: number;
    acelerador(velocidad: number): string;
    freno(): string;
    girar(direccion: 'left' | 'right'): string;
}

class Auto implements vehiculo {
   marca!: string;
   modelo!: string;
   puertas!: number;


   acelerador(velocidad: number): string {
      throw new Error("Method not implemented.");
   }
   freno(): string {
      throw new Error("Method not implemented.");
   }
   girar(direccion: "left"|"right"): string {
      throw new Error("Method not implemented.");
   }
}

```

### genericos

Los genéricos son plantillas de código que puede definir y reutilizar en todo el código base

**cuando usar genericos**

- Funcione con varios tipos de datos.
- Use ese tipo de datos en varios lugares.

```typeScript
// ejemplo 1
function getArray<T>(items : T[]) : T[] {
    return new Array<T>().concat(items);
}
let numberArray = getArray<number>([5, 10, 15, 20]);

// ejemplo 2
function identity<T, U> (value: T, message: U) : T {
    console.log(message);
    return value
}

let returnNumber = identity<number, string>(100, 'Hello!');
let returnString = identity<string, string>('100', 'Hola!'
```

### Uso de restricciones de tipos con genéricos

cundo se tiene type ValidTypes = string | number;
y se quiere realizar una operacion value + value suma genera problemas porque para un tipo de tado numero se realiza suma y para un string uns concatenacion , esto se soluciona de la siguiente manera , utilizando `if y typeod`

```typeScript
type ValidTypes = string | number;
function identity<T extends ValidTypes, U> (value: T, message: U) {
   // Return type is inferred
    let result: ValidTypes = '';
    let typeValue: string = typeof value;

    if (typeof value === 'number') {           // Is it a number?
        result = value + value;                // OK
    } else if (typeof value === 'string') {    // Is it a string?
        result = value + value;                // OK
    }

    console.log(`The message is ${message} and the function returns a ${typeValue} value of ${result}`);

    return result
}

let numberValue = identity<number, string>(100, 'Hello');
let stringValue = identity<string, string>('100', 'Hello');

console.log(numberValue);       // Returns 200
console.log(stringValue);       // Returns 100100
```

### Declaración de una interfaz genérica

```typeScript
interface Identity<T, U> {
    value: T;
    message: U;
}
let returnNumber: Identity<number, string> = {
    value: 25,
    message: 'Hello!'
}
```

### Declaración de una interfaz genérica como un tipo de función

```typeScript
interface ProcessIdentity<T, U> {
    (value: T, message: U): T;
}
function processIdentity<T, U> (value: T, message: U) : T {
    console.log(message);
    return value
}
let processor: ProcessIdentity<number, string> = processIdentity;
let returnNumber1 = processor(100, 'Hello!');   // OK
```

### clase generica

```typeScript
class processIdentity<T, U> {
    private _value: T;
    private _message: U;
    constructor(value: T, message: U) {
        this._value = value;
        this._message = message;
    }
    getIdentity() : T {
        console.log(this._message);
        return this._value
    }
}
let processor = new processIdentity<number, string>(100, 'Hello');
processor.getIdentity();      // Displays 'Hello'
```
