# patternDesing Javascript
### Constructor pattern:
Creamos una clase base para que la demas clases herenden de la clase base. 
~~~
class Persona {
  constructor(nombre, apellido){
    this.nombre = nombre;
    this.apellido = apellido;
  }
}
class Estudiante extends Persona{
        constructor(nombre, apellido, escuela){
          super(nombre, apellido);
          this.escuela = escuela;

        }
}
const estudiante = new Estudiante('Moises','Nieto', 'Ins el saber');
console.log(estudiante);
~~~

### Singleton pattern:
no permite instanciar multiples objetos con la misma clase.
~~~
let instancia = null
class Cliente {
  constructor(nombre, apellido){
    if(!instancia){          
      this.nombre = nombre;
      this.apellido = apellido;
      instancia = this;
    }else{
      return instancia;//y si ya hay algo me devolvera el objeto ya creado con anteoridad.
    }

  }
}
const cliente = new Cliente('eddy', 'nieto');
console.log(cliente);  //creamo el objeto cliente 
const cliente2 = new Cliente('andres', 'nieto');
console.log(cliente2); // cuando creamo el segundo nos devolvera la primera instancia creada 
                        // asi evitamos crear mas objeto de una misma clase
~~~

### Factory pattern:
Crea objetos basados en diversas condiciones.
~~~
class Pizza {
  constructor(sabor, tamaño){
    this.sabor= sabor;
    this.tamaño= tamaño;
  }
  cocinarPizza(){
    return `He cocinado un pizza de sabor: ${this.sabor} y es de tamaño: ${this.tamaño} `;
  }
}
class Pizzeria{
    prepararPizza(sabor, tamaño){
      switch(sabor){
        case 'queso':
          return new Pizza('queso', tamaño)

        default:
          return;
      }
    }
}
const Pizza1 = new Pizzeria();
const pizzaDeQueso = Pizza1.prepararPizza('queso', 'familiar');
console.log(pizzaDeQueso.cocinarPizza()); // He cocinado un pizza de sabor: queso y es de tamaño: familiar 
~~~
### Module pattern:
Este patron  nos ayuda a organizar y aislar las distintas funciones y clases con las que trabajamos usando lo import y export en la nuevas versiones de javascript. 
~~~
//version moderna usando export
// si queremos usar esta funcion en otro archivo usamos import

/*
const pizza = sabor =>{
  console.log(sabor);
}
export default pizza();
*/
//version antigua 
// si queremos usar la variable y funciones en otro archivo usamos 
// module.sabor si queremos motrar el sabor
// module.cocinarPizza() si querremos usar la funcion 

/*
const module = (function(){
          const sabor = '4 queso';
           function cocinarPizza(){
             console.log('Me gusta la pizza de 4 queso');
           }

           return {
             sabor,
              cocinarPizza
            }
})();
~~~
### Mixin pattern:
Este patrón nos permite añadir mas funcionalidades, A una clase existente sin tener que modificar la clase.  
~~~
class pizza {
  constructor(sabor, tamaño){
    this.sabor= sabor;
    this.tamaño= tamaño;
  }
}
const funcionesPizza={
  mostrarsabro(){
    console.log(`me gusta mucho la pizza ${this.sabor}`);
  },
  mostrarTamaño(){
    console.log(`me gusta mucho la pizza ${this.tamaño}`);
  }
}
//para añadir funcionalidades a una clase usamos: el object.assign

Object.assign(Pizza.prototype, funcionesPizza);


const pizza = new pizza('4 queso', 'familiar');
pizza.mostrarsabro()
pizza.mostrarTamaño()
~~~

### Namespace pattern:
Nos ayuda a evitar la colision de nombre con otros objetos y varibales del  scope global , Creamo un objeto global donde estaran nuestras funciones etc. 
~~~
const storeGame = {};
storeGame.games =[
  {
    gameName:'resident evil 8',
    price: 20
  },
  {
    gameName:'last of us',
    price: 60
  },
  {
    gameName:'mario car',
    price: 80
  }
]
storeGame.fnc ={
  showGame: games =>{
    games.forEach((game, index ) => {
      console.log(`${index}: ${game.gameName}`)
    });

  }
}
const {games} = storeGame;

storeGame.fnc.showGame(games);/*
                            0: resident evil 8
                            1: last of us
                            2: mario car
                                        */
~~~
