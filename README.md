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
