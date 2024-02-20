# **Markdown**

---


## *Pregunta 1*
**Tus expectativas antes de aprender POO. ¿Qué creías que ibas a aprender y para qué creías que iba a servir lo que ibas a ver sobre este tema?**

En primer lugar yo no había visto mucho **POO** anteriormente, aunque si que es cierto que el tema de funciones yo ya las había visto anteriormente en otro lenguaje, **Python**, y ya tenía un poco idea del tema. 
La verdad que este tema me parece el más importante que hemos visto hasta la fecha, debiido a que ya nos permite hacer proyectos más grandes, con sus distintas clases y relaciones entre estas.


---


## *Pregunta 2*
**¿Qué has aprendido durante las dos unidades?**

En primer lugar la implementación de **funciones** en **Java**, en mi caso me costo un poco la implementación de estas y de los **contructores**, debido a que yo ya tenía una idea del concepto pero en **Python**. Por otra parte las diferentes **relaciones** entre clases me han parecido muy interesantes, ya que en alguna de las primeras prácticas de progrmación orientada a objetos ya las habiamos utilizado pero sin saber el concepto teórico,**asociación**, **agregación** y **composición**.  También esta el concepto de la **herencia** que permite determinar superclases y subclases dentro de un mismo proyecto y las distintas relaciones entre las funciones. Otro concepto que hemos aprendido es el tema de la **visbilidad** que nos permite declarar una propiedad agregandole diferentes grados de visibilidad como private,friendly,protected y public. En último lugar se encuentra el concepto de las **interfaces**, que todavía no hemos entrado en detalle respecto a la realización de prácticas.


---


## *Pregunta 3*
**Elige dos ejercicios de las prácticas que te hayan sido, para ti, los más importantes. Indica por qué y explica cómo lo has resuelto u lo que has aprendido con ellos**

El primer ejercicio es el de las **colas**, debido a su gran importancia por el uso de arrays, y a la hora de jugar con ellos sacando y metiendo elementos en estos. Me ha parecido muy interesante por que ha sido el primer proyecto con un nivel de dificultad más alto en este tema de **POO**. 
Lo primero que he hecho ha sido crear un constructor con el que le doy dos valores a las dos propiedades en este caso un contador y un array de Strings.
Luego se crean las funciones de sacar elemento y la de meter elemento que en mi opinión son de gran importacia debido a que se seguirán usando en el futuro. La primera función llamada add sirve para introducir elementos en el array, con la propiedad contador siempre que sea menor que el tamaño del array nos permite introducir los elementos y este se incrementa. La segunda función llamada poll saca el primer elemento del array, yo en este caso lo que hice fue utilizar un array auxiliar para poner todos los elementos menos el primero y después pasarlo otra vez al array de origen, con los conocimientos que tengo ahora la verdad que lo haría de otra forma diferente, que sería sacar el primer elemento y correr el array una posición, sin necesidad de utilizar un array auxiliar.
Por último está la función llamada list que nos muestra el contenido del array.

```java
public class Cola {
    public String[] cola;
    private int Contf ;

    public Cola() {
        this.cola = new String[50];
        this.Contf=0;
    }

    public void add(String elemento) {
        if (Contf < cola.length) {
            cola[Contf] = elemento;
            Contf++;
        }
    }

    public boolean empty() {
        return Contf == 0;
    }

    public String poll() {
        int cont = 1;
        String aux;
        aux = cola[0];
        String []cola2=new String[50];
        if (!empty()) {
            for (int i = 0; i < cola2.length; i++) {
                if(cola[cont]!=null){
                cola2[i] = cola[cont];
                cont++;
                }
                else{
                    Contf=i;
                    break;
                }
            }
            cont=0;
            for(int i=0;i<cola.length;i++){
                cola[i]=cola2[cont];
                cont++;
            }
            return aux;
           
        } else {
            return "0";
        }
         /*segunda opcion
             * String aux;
               aux = cola[0];
               for(int i=1;i<Contf;i++){
                cola[i-1]=cola[i]
               }
               Contf--;
             */
    }
    public void list(){
        for(int i=0;i<cola.length;i++){
            System.out.println(cola[i]);
        }
    }
    public void setEmpty(){
        for(int i=0;i<cola.length;i++){
            cola[i]=null;
        }
    }
    public int available(){
        
        return cola.length-Contf;
    }

}
```

El segundo ejercicio es el de los **ordenadores**, debido a que en esa práctica se introducen los conceptos de **herencia**, **asociación**, **agregación** y **composición**
En esta práctica la primera clase que he creado ha sido la de la cámara debido a su sencillez, la siguiente clase es la de ordenador debido a que es una superclase con sus diferentes subclases, después he creado la clase móvil, en la que existe una relación composición con la cámara, más tarde se crea la clase, la clase portátil y por último la clase empresa, que emplea métodos similares al de la pila y la cola. Podemos observar una relación de asociación entre la clase empresa y la clase ordenador.

``` java
public class App1 {
    public static void main(String[] args) {
        Empresa e1=new Empresa("InfoValladolid S.A.");
        int con=1;
        int c=1;
        for(int i=2;i<=25;i+=2){
            Ordenador o=new Ordenador("PC"+con,16,1024,"i5");
            e1.añadirordenador(o);
            con++;
        }
        for(int i=1;i<=25;i+=2){
           Portatil p=new Portatil("PC"+con, 16, 1024, "i5", 3);
           e1.añadirordenador(p);
           con++;
        }

        
        for(int i=1;i<=50;i++){
            Movil m=new Movil("MB"+c, 8, 256, " Snapdragon 8 Gen 2", 2.2, 12, "Carl Zeiss");
            e1.añadirordenador(m);
            c++;
        }
        e1.escribir();

        e1.encenderordenadores();
        for(int i=0;i<e1.cont;i++){
            if(!(e1.lista[i] instanceof Portatil && e1.lista[i] instanceof Movil )){
             e1.retirarordenador(e1.lista[i]);
                con--;
            }
        }
        e1.escribir();


        for(int i=1;i<=20;i++){
            Portatil p=new Portatil("PC"+con, 16, 1024, "i5", 3);
            e1.añadirordenador(p);
            con++;
        }
        System.out.println("--------------------------------------");
        e1.escribir();
        System.out.println(".....................................................");
        e1.revolver();
        e1.escribir();
        for(int i=0;i<e1.lista.length;i++){
            if(e1.lista[i] instanceof Portatil){
                e1.lista[i].hd=2048;
            }
        }
        e1.escribir();
       



    }
}
```

----


## *Pregunta 4*
**Explica tus conclusiones en este momento sobre estas dos unidades: Qué has aprendido realmente, qué utilidad le ves y di lo más positivo que has adquirido en estas dos unidades y lo que menos te ha gustado.**

En mi opinión son los dos temas más importantes que hemos visto hasta la fecha, también los más complicados. Hemos visto multitud de conceptos que de primeras pueden ser complejos pero con las prácticas se van asimilando cada vez más. Para mi lo más positivo en general ha sido todo, ya que es un tema que me gusta bastante y nos da un amplio abaníco a la hora de desarrollar las prácticas. Por último lo que menos me ha gustado ha sido el tema de interfaces, debido a que todavía esta muy reciente y falta asimilarlo.





