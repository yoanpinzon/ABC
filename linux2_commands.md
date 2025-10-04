# 💻 Explorando Comandos Esenciales en bash para Unix/Linux

A medida que avanzamos en nuestro recorrido por `bash`, profundizaremos en comandos esenciales para la manipulación de texto y la interacción con el usuario. 

Exploraremos herramientas clave como `grep`, `cut`, `sort`, y `sed`, que permiten buscar, ordenar datos y editar archivos de texto. Finalmente, aplicaremos estos conceptos en la creación de un script de administración para un banco (`banco.sh`)."

## 1. Leer Entradas del Usuario con `read`

El comando `read` es fundamental cuando necesitamos capturar datos ingresados por el usuario. Este comando es útil en muchos contextos, como cuando necesitamos obtener un nombre, un número o cualquier otra información.

**Ejemplo 1: Capturar el nombre del usuario**

```bash
cd ~/workspace
```

```bash
echo -n "Por favor, ingresa tu nombre: "
read nombre
echo "Hola, $nombre!"
```
<details><summary>🏃 How to Run</summary>
  
Intenta este ejemplo en Replit para ver cómo interactúa el script contigo. Lo puedes llamar `p1.sh`. 

**1. Crear el archivo `p1.sh`:**
   * Para crear el archivo `p1.sh`, abre la terminal en Replit y escribe:
   ```bash
   code p1.sh
   ```
   * Esto abrirá el editor de texto. En él, escribe el siguiente código:

   ```bash
   echo -n "Por favor, ingresa tu nombre: "
   read nombre
   echo "Hola, $nombre!"
   ```

**2. Cambiar los permisos:**
   * En la terminal, ejecuta el siguiente comando para otorgar permisos de ejecución al archivo:

   ```bash
   chmod +x p1.sh
   ```

**3. Ejecutar el script:**
   * Ahora puedes ejecutar el script como un comando:

   ```bash
   ./p1.sh
   ```

**4. Interactuar con el script:**
   * Al ejecutar el script, verás el mensaje "Por favor, ingresa tu nombre:". Escribe tu nombre y presiona Enter. El script te saludará con un mensaje personalizado.

</details>

Este proceso no solo te permitirá ejecutar el script, sino que también te mostrará cómo interactuar con él, haciendo que la experiencia sea más dinámica y motivadora. ¡Inténtalo y disfruta de la magia de `bash`!


**Qué sucede:**
- `echo -n` muestra el mensaje sin un salto de línea.
- `read nombre` captura la entrada y la guarda en la variable `nombre`.
- `echo "Hola, $nombre!"` saluda al usuario usando su nombre.

---

**Ejemplo 2: Sumar dos números**

```bash
echo -n "Por favor, ingresa el primer número: "
read num1
echo -n "Por favor, ingresa el segundo número: "
read num2
suma=$((num1 + num2))
echo "La suma de $num1 y $num2 es: $suma"
```

<details><summary>🏃 How to Run</summary>

Intenta este ejemplo en Replit para ver cómo interactúa el script contigo. Lo puedes llamar `sum.sh`. 

**1. Crear el archivo `sum.sh`:**
   * Para crear el archivo `sum.sh`, abre la terminal en Replit y escribe:
   ```bash
   code sum.sh
   ```
   * Esto abrirá el editor de texto. En él, escribe el siguiente código:

   ```bash
   echo -n "Por favor, ingresa el primer número: "
   read num1
   echo -n "Por favor, ingresa el segundo número: "
   read num2
   suma=$((num1 + num2))
   echo "La suma de $num1 y $num2 es: $suma"
   ```

**2. Cambiar los permisos:**
   * En la terminal, ejecuta el siguiente comando para otorgar permisos de ejecución al archivo:

   ```bash
   chmod +x sum.sh
   ```

**3. Ejecutar el script:**
   * Ahora puedes ejecutar el script como un comando:

   ```bash
   ./sum.sh
   ```

**4. Interactuar con el script:**
   * Al ejecutar el script, se te pedirá que ingreses dos números. Luego, el script calculará e imprimirá la suma de ambos.

</details>

Este proceso te permitirá crear un script básico que realiza una operación matemática simple en `bash`. Es un excelente punto de partida para comprender cómo se puede interactuar con el usuario y procesar datos en el shell. ¡Dale una oportunidad y experimenta con diferentes números para ver cómo funciona!

---

## 2. Encontrar Textos en Archivos con `grep`

El comando `grep` es una herramienta poderosa para buscar patrones de texto en archivos. Imagina que tienes un archivo de texto y necesitas encontrar todas las líneas que contienen una palabra específica.

<details><summary>🔎 Discovery: Origen del comando grep</summary>
  
**¿Que significa `grep`?**

El nombre `grep` proviene de un comando del antiguo editor de texto `ed` en Unix, que era `g/re/p`. Este comando significaba:

* **g:** global (buscar en todo el archivo)
* **re:** regular expression (expresión regular)
* **p:** print (imprimir)

En resumen, `g/re/p` buscaba globalmente en un archivo, líneas que coincidieran con una expresión regular y las imprimía.

**¿Por qué se popularizó como `grep` y no se mantuvo el nombre original?**

Con el tiempo, la funcionalidad de buscar con expresiones regulares se volvió tan útil que se separó del editor `ed` y se convirtió en un comando independiente. Al acortar `g/re/p` a `grep`, se obtuvo un nombre corto y fácil de recordar.

</details>

**Ejemplo 3: Buscar palabras en un archivo**

Este ejemplo te muestra cómo utilizar el comando `grep` para buscar una palabra específica dentro de un archivo de texto en Bash. Es una forma poderosa y eficiente de filtrar información.


```bash
echo -e "manzana\npera\nuva\nmanzana" > frutas.txt
grep "manzana" frutas.txt
```

<details><summary>🏃 How to Run</summary>

**1. Crear el archivo `frutas.sh`:**
   * Para crear el archivo `frutas.sh`, abre la terminal en Replit y escribe:
   ```bash
   code frutas.sh
   ```
   * Esto abrirá el editor de texto. En él, escribe el siguiente código:

   ```bash
   echo -e "manzana\npera\nuva\nmanzana" > frutas.txt
   grep "manzana" frutas.txt
   ```

**2. Cambiar los permisos:**
   * En la terminal, ejecuta el siguiente comando para otorgar permisos de ejecución al archivo:

   ```bash
   chmod +x frutas.sh
   ```

**3. Ejecutar el script:**
   * Ahora puedes ejecutar el script como un comando:

   ```bash
   ./frutas.sh
   ```

**4. Ver el resultado:**
   * Al ejecutar el script, se creará un archivo llamado `frutas.txt` que contiene varias frutas. Luego, el script buscará la palabra "manzana" en el archivo y mostrará todas las líneas que la contienen.

</details>

<details>
<summary>🔧 Hints: Mostrar Números de Línea con grep</summary>

### ¿Quieres saber en qué línea exacta se encuentra una coincidencia?

Utiliza la opción `-n` junto con el comando `grep`. Esto hará que se muestre el número de línea antes de cada línea que coincida.

**Ejemplo:**
```bash
grep -n "manzana" frutas.txt
```
Si en el archivo `frutas.txt` tienes varias líneas con la palabra "manzana", `grep -n` te dirá en cuál de ellas se encuentra cada una. 

</details>

**Qué sucede:**
- `echo -e` crea un archivo `frutas.txt` con varias líneas.
- `grep "manzana" frutas.txt` busca todas las líneas que contienen "manzana".

Este ejemplo te muestra cómo `grep` puede localizar información rápidamente en un archivo.

### Opciones adicionales:
- `grep -i "manzana" frutas.txt`: Ignora mayúsculas y minúsculas.
- `grep -v "manzana" frutas.txt`: Muestra todas las líneas que **no** contienen "manzana".

---

## 3. Ordenar Contenidos con `sort`

¿Alguna vez has necesitado organizar una lista? Con `sort`, puedes ordenar líneas de texto alfabéticamente o numéricamente.

**Ejemplo 4: Ordenar una lista de frutas**
```bash
echo -e "pera\nuva\nmanzana\nnaranja" > frutas.txt
sort frutas.txt
```

<details><summary>🏃 How to Run</summary>

**1. Crear el archivo `ordenar.sh`:**
   * Para crear el archivo `ordenar.sh`, abre la terminal en Replit y escribe:
   ```bash
   code ordenar.sh
   ```
   * Esto abrirá el editor de texto. En él, escribe el siguiente código:

   ```bash
   echo -e "pera\nuva\nmanzana\nnaranja" > frutas.txt
   sort frutas.txt
   ```

**2. Cambiar los permisos:**
   * En la terminal, ejecuta el siguiente comando para otorgar permisos de ejecución al archivo:

   ```bash
   chmod +x ordenar.sh
   ```

**3. Ejecutar el script:**
   * Ahora puedes ejecutar el script como un comando:

   ```bash
   ./ordenar.sh
   ```

**4. Ver el resultado:**
   * Al ejecutar el script, se creará un archivo llamado `frutas.txt` con una lista de frutas desordenadas. Luego, el comando `sort` ordenará alfabéticamente el contenido del archivo y mostrará la lista ordenada en la terminal.

</details>

**Qué sucede:**
- `sort frutas.txt` organiza las líneas del archivo `frutas.txt` alfabéticamente.

### Opciones adicionales:
- `sort -r frutas.txt`: Ordena en orden inverso.
- `sort -t ':' -k2,2 archivo.txt`: Ordena por una clave específica en archivos con delimitadores.


**Ejemplo 5: Ordenar estudiantes por nombre y nota**

```bash
#!/bin/bash
echo "John:4.2" >> estudiantes.txt
echo "Mary:3.8" >> estudiantes.txt
echo "David:4.5" >> estudiantes.txt
echo "Emily:3.9" >> estudiantes.txt
echo "Michael:4.1" >> estudiantes.txt
echo "Jessica:4.7" >> estudiantes.txt
echo "Matthew:3.6" >> estudiantes.txt
echo "Ashley:4.3" >> estudiantes.txt
echo "Christopher:4.9" >> estudiantes.txt
echo "Sarah:4.0" >> estudiantes.txt

sort estudiantes.txt > estudiantes_por_nombre.txt
sort -t ':' -k2n estudiantes.txt > estudiantes_por_nota.txt

echo "Archivos creados: estudiantes_por_nombre.txt y estudiantes_por_nota.txt"
```

<details><summary>🏃 How to Run</summary>

**1. Crear el archivo `notas.sh`:**
   * Para crear el archivo `notas.sh`, abre la terminal en Replit y escribe:
   ```bash
   code notas.sh
   ```
   * Esto abrirá el editor de texto. En él, escribe el siguiente código:

   ```bash
   #!/bin/bash
   echo "John:4.2" >> estudiantes.txt
   echo "Mary:3.8" >> estudiantes.txt
   echo "David:4.5" >> estudiantes.txt
   echo "Emily:3.9" >> estudiantes.txt
   echo "Michael:4.1" >> estudiantes.txt
   echo "Jessica:4.7" >> estudiantes.txt
   echo "Matthew:3.6" >> estudiantes.txt
   echo "Ashley:4.3" >> estudiantes.txt
   echo "Christopher:4.9" >> estudiantes.txt
   echo "Sarah:4.0" >> estudiantes.txt

   sort estudiantes.txt > estudiantes_por_nombre.txt
   sort -t ':' -k2n estudiantes.txt > estudiantes_por_nota.txt

   echo "Archivos creados: estudiantes_por_nombre.txt y estudiantes_por_nota.txt"
   ```

**2. Cambiar los permisos:**
   * En la terminal, ejecuta el siguiente comando para otorgar permisos de ejecución al archivo:

   ```bash
   chmod +x notas.sh
   ```

**3. Ejecutar el script:**
   * Ahora puedes ejecutar el script como un comando:

   ```bash
   ./notas.sh
   ```

**4. Ver los resultados:**
   * Al ejecutar el script, se creará un archivo llamado `estudiantes.txt` con una lista de estudiantes y sus notas. Luego, el script ordenará el archivo por nombre y por nota, generando dos archivos: `estudiantes_por_nombre.txt` (ordenado por nombre) y `estudiantes_por_nota.txt` (ordenado por nota). Finalmente, mostrará un mensaje indicando que los archivos han sido creados.

</details>

**Qué sucede:**
* `echo`: Escribe texto en un archivo.
* `sort`: Ordena las líneas de un archivo.
* `-t ':'`: Indica a `sort` que use el carácter `:` como separador entre los campos.
* `-k2n`: Le dice a `sort` que ordene según el segundo campo (la nota) y que lo trate como un número.
* `>`: Redirige la salida de un comando a un archivo.

**Ejemplo 6: Ordenar estudiantes por id desendentemente**

```bash
#!/bin/bash
echo "John:4.2:34567" > estudiantes.txt
echo "Mary:3.8:23456" >> estudiantes.txt
echo "David:4.5:37653" >> estudiantes.txt
echo "Emily:3.9:45678" >> estudiantes.txt
echo "Michael:4.1:12345" >> estudiantes.txt
echo "Jessica:4.7:56789" >> estudiantes.txt
echo "Matthew:3.6:78901" >> estudiantes.txt
echo "Ashley:4.3:67890" >> estudiantes.txt
echo "Christopher:4.9:89012" >> estudiantes.txt
echo "Sarah:4.0:01234" >> estudiantes.txt

sort -t ':' -k3nr estudiantes.txt > estudiantes_por_id_desc.txt

echo "Archivo creado: estudiantes_por_id_desc.txt"
```

<details><summary>🏃 How to Run</summary>

**1. Crear el archivo `notas2.sh`:**
   * Para crear el archivo `notas2.sh`, abre la terminal en Replit y escribe:
   ```bash
   code notas2.sh
   ```
   * Esto abrirá el editor de texto. En él, escribe el siguiente código:

   ```bash
   #!/bin/bash
   echo "John:4.2:34567" > estudiantes.txt
   echo "Mary:3.8:23456" >> estudiantes.txt
   echo "David:4.5:37653" >> estudiantes.txt
   echo "Emily:3.9:45678" >> estudiantes.txt
   echo "Michael:4.1:12345" >> estudiantes.txt
   echo "Jessica:4.7:56789" >> estudiantes.txt
   echo "Matthew:3.6:78901" >> estudiantes.txt
   echo "Ashley:4.3:67890" >> estudiantes.txt
   echo "Christopher:4.9:89012" >> estudiantes.txt
   echo "Sarah:4.0:01234" >> estudiantes.txt

   sort -t ':' -k3nr estudiantes.txt > estudiantes_por_id_desc.txt

   echo "Archivo creado: estudiantes_por_id_desc.txt"
   ```

**2. Cambiar los permisos:**
   * En la terminal, ejecuta el siguiente comando para otorgar permisos de ejecución al archivo:

   ```bash
   chmod +x notas2.sh
   ```

**3. Ejecutar el script:**
   * Ahora puedes ejecutar el script como un comando:

   ```bash
   ./notas2.sh
   ```

**4. Ver los resultados:**
   * Al ejecutar el script, se creará un archivo llamado `estudiantes.txt` con una lista de estudiantes, sus notas y sus IDs. Luego, el script ordenará el archivo por ID en orden descendente, generando un archivo `estudiantes_por_id_desc.txt`. Finalmente, mostrará un mensaje indicando que el archivo ha sido creado.

</details>

**Qué sucede:**
* `echo`: Escribe texto en un archivo.
* `sort`: Ordena las líneas de un archivo.
* `-t ':'`: Indica a `sort` que use el carácter `:` como separador entre los campos.
* `-k3nr`: Le dice a `sort` que ordene según el tercer campo (el ID), en orden numérico descendente.
   * `-k3`: Indica que la ordenación se realizará sobre el tercer campo (el ID).
   * `-n`: Asume que los elementos del tercer campo son números.
   * `-r`: Invierte el orden, por lo que se ordenará de mayor a menor.
 
* `>`: Redirige la salida de un comando a un archivo.

---

## 4. Manipulación de Texto con `cut`

El comando `cut` se utiliza para extraer secciones específicas de texto en cada línea de un archivo. Es especialmente útil cuando trabajas con archivos que tienen datos estructurados.

**Ejemplo 7: Extraer partes de un texto**

Este ejemplo muestra cómo utilizar el comando `cut` para extraer una columna específica de un archivo de texto, una técnica útil para manejar y analizar datos estructurados.

```bash
echo -e "manzana:rojo\npera:verde\nuva:morada" > colores.txt
cut -d ':' -f1 colores.txt
```
<details><summary>🏃 How to Run</summary>

**1. Crear el archivo `extraer.sh`:**
   * Para crear el archivo `extraer.sh`, abre la terminal en Replit y escribe:
   ```bash
   code extraer.sh
   ```
   * Esto abrirá el editor de texto. En él, escribe el siguiente código:

   ```bash
   echo -e "manzana:rojo\npera:verde\nuva:morada" > colores.txt
   cut -d ':' -f1 colores.txt
   ```

**2. Cambiar los permisos:**
   * En la terminal, ejecuta el siguiente comando para otorgar permisos de ejecución al archivo:

   ```bash
   chmod +x extraer.sh
   ```

**3. Ejecutar el script:**
   * Ahora puedes ejecutar el script como un comando:

   ```bash
   ./extraer.sh
   ```

**4. Ver el resultado:**
   * Al ejecutar el script, se creará un archivo llamado `colores.txt` con una lista de frutas y sus colores, separados por dos puntos. Luego, el comando `cut -d ':' -f1 colores.txt` extraerá y mostrará la primera parte de cada línea (la fruta) en la terminal.

</details>

**Qué sucede:**
- `cut -d ':' -f1 colores.txt` extrae la primera parte de cada línea, usando `:` como delimitador.

Este comando es excelente cuando trabajas con archivos que contienen datos separados por un carácter específico.

---

## 5. Editando Textos con `sed`

El comando `sed` es una herramienta poderosa para realizar ediciones en archivos de texto. A diferencia de `grep`, que solo busca patrones, `sed` te permite modificar el texto de acuerdo a tus necesidades.

<details><summary>🔎 Discovery: Origen del comando sed</summary>

**¿Que significa `sed`?**

A diferencia de `grep`, cuyo nombre proviene directamente del comando `g/re/p` en el editor de texto `ed`, el origen del nombre `sed` no es tan elaborado. `sed` se deriva de Stream Editor (Editor de Flujo), un nombre descriptivo que refleja su función principal: editar texto en un flujo de datos de manera automática y no interactiva.

</details>

**Ejemplo 8: Reemplazar texto en un archivo**

Supongamos que tenemos un archivo de texto llamado `frutas.txt` y queremos reemplazar todas las ocurrencias de "manzana" por "kiwi".

```bash
echo -e "manzana\npera\nuva\nmanzana" > frutas.txt
sed -i 's/manzana/kiwi/g' frutas.txt
```

<details><summary>🏃 How to Run</summary>

**1. Crear el archivo `frutas2.sh`:**
* Abre tu terminal y escribe:
```bash
code frutas2.sh
```
* Pega el siguiente código dentro del archivo:
```bash
echo -e "manzana\npera\nuva\nmanzana" > frutas.txt
sed -i 's/manzana/kiwi/g' frutas.txt
```

**2. Ejecutar el script:**
```bash
bash frutas2.sh
```

**3. Ver el resultado:**
* Al ejecutar el script, se creará un archivo llamado `frutas.txt` con las frutas. Luego, el comando `sed` reemplazará todas las "manzana" por "kiwi" directamente en el archivo.

</details>

**Qué sucede:**
* `echo -e "manzana\npera\nuva\nmanzana" > frutas.txt`: Crea un archivo llamado `frutas.txt` y escribe las frutas en él.
* `sed -i 's/manzana/kiwi/g' frutas.txt`: 
    * `-i`: Indica que el cambio se hará directamente en el archivo (en lugar de mostrarlo en la salida).
    * `s/manzana/kiwi/g`: Realiza una sustitución (s): busca "manzana" y la reemplaza por "kiwi" en todo el archivo (g).

**Ejemplo 9: Eliminar líneas que contienen un patrón**

Ahora, supongamos que queremos eliminar todas las líneas que contienen la palabra "uva" del archivo `frutas.txt`.

```bash
echo -e "manzana\npera\nuva\nmanzana" > frutas.txt
sed -i '/uva/d' frutas.txt
```

<details><summary>🏃 How to Run</summary>

**1. Crear el archivo `frutas3.sh`:**
* Abre tu terminal y escribe:
```bash
code frutas3.sh
```
* Pega el siguiente código dentro del archivo:
```bash
echo -e "manzana\npera\nuva\nmanzana" > frutas.txt
sed -i '/uva/d' frutas.txt
```

**2. Ejecutar el script:**
```bash
bash frutas3.sh
```

**3. Ver el resultado:**
* Al ejecutar el script, se eliminarán todas las líneas que contengan "uva" del archivo `frutas.txt`.

</details>

**Qué sucede:**
* `sed -i '/uva/d' frutas.txt`: 
    * `-i`: Indica que el cambio se hará directamente en el archivo.
    * `/uva/`: Busca las líneas que contienen "uva".
    * `d`: Elimina las líneas que coinciden con el patrón.

**En resumen:**

Estos dos ejemplos muestran cómo `sed` puede utilizarse para realizar modificaciones básicas en archivos de texto: reemplazar texto y eliminar líneas.

## 6. Manipulando Textos con `awk`

El comando `awk` es una herramienta poderosa y flexible para procesar y analizar texto en archivos. A diferencia de `sed`, que se centra en la edición de texto, `awk` es ideal para extraer y manipular datos basados en patrones y estructuras de texto.

<details><summary>🔎 Discovery: Origen del comando awk</summary>

**¿Que significa `awk`?**

A diferencia de `grep` y `sed`, que tienen orígenes más directos en el ecosistema de Unix, el comando `awk` fue creado específicamente como un lenguaje de programación para el procesamiento de patrones y textos.

**¿Por qué "awk"?**

A diferencia de otros comandos de Unix, que a menudo tenían nombres cortos y arbitrarios, `awk` fue nombrado en honor a sus autores:

- **Alfred Aho**
- **Peter Weinberger**
- **Brian Kernighan**

</details>


**Ejemplo 10: Extraer el segundo campo de un archivo**

```bash
echo -e "John:4.2:34567\nMary:3.8:23456\nDavid:4.5:37653" > estudiantes.txt
awk -F ':' '{print $2}' estudiantes.txt
```

<details><summary>🏃 How to Run</summary>

**1. Crear el archivo `notas3.sh`:**
* Abre tu terminal y escribe:
```bash
code notas3.sh
```
* Pega el siguiente código dentro del archivo:
```bash
echo -e "John:4.2:34567\nMary:3.8:23456\nDavid:4.5:37653" > estudiantes.txt
awk -F ':' '{print $2}' estudiantes.txt
```

**2. Ejecutar el script:**
```bash
bash notas3.sh
```

**3. Ver el resultado:**
* Al ejecutar el script, `awk` imprimirá las notas de los estudiantes en la salida estándar.

</details>

**Qué sucede:**
* `echo -e "John:4.2:34567\nMary:3.8:23456\nDavid:4.5:37653" > estudiantes.txt`: Crea un archivo llamado `estudiantes.txt` con los datos de los estudiantes.
* `awk -F ':' '{print $2}' estudiantes.txt`:
  * `-F ':'`: Indica que el campo delimitador es `:` (dos puntos).
  * `'{print $2}'`: Imprime el segundo campo de cada línea, que en este caso corresponde a las notas.

**Ejemplo 11: Calcular el promedio de las notas**

```bash
echo -e "John:4.2:34567\nMary:3.8:23456\nDavid:4.5:37653" > estudiantes.txt
awk -F ':' '{sum += $2; count++} END {print "Promedio:", sum/count}' estudiantes.txt
```

<details><summary>🏃 How to Run</summary>

**1. Crear el archivo `promedio.sh`:**
* Abre tu terminal y escribe:
```bash
code promedio.sh
```
* Pega el siguiente código dentro del archivo:
```bash
echo -e "John:4.2:34567\nMary:3.8:23456\nDavid:4.5:37653" > estudiantes.txt
awk -F ':' '{sum += $2; count++} END {print "Promedio:", sum/count}' estudiantes.txt
```

**2. Cambiar los permisos:**
   * En la terminal, ejecuta el siguiente comando para otorgar permisos de ejecución al archivo:

   ```bash
   chmod +x promedio.sh
   ```

**3. Ejecutar el script:**
```bash
bash promedio.sh
```

**4. Ver el resultado:**
* Al ejecutar el script, `awk` calculará e imprimirá el promedio de las notas.

</details>

**Qué sucede:**
* **`awk -F ':'`:**
  * `awk`: Es una herramienta de procesamiento de texto que permite realizar acciones sobre archivos de texto línea por línea.
  * `-F ':'`: Indica a `awk` que el delimitador de los campos en cada línea es el carácter `:`. Es decir, los datos en cada línea están separados por dos puntos.

* **`'{sum += $2; count++}'`:**
  * `{ ... }`: Este bloque de código se ejecuta para cada línea del archivo.
  * `sum += $2`: Suma el valor del segundo campo de la línea actual (la nota) a una variable llamada `sum`. Esta variable se utiliza para acumular la suma total de todas las notas.
  * `count++`: Incrementa en uno una variable llamada `count`. Esta variable se utiliza para contar el número total de líneas procesadas (es decir, el número de estudiantes).

* **`END {print "Promedio:", sum/count}`:**
  * `END`: Este bloque de código se ejecuta al final, después de procesar todas las líneas del archivo.
  * `print "Promedio:", sum/count`: Imprime en la pantalla el mensaje "Promedio:" seguido del resultado de dividir la suma total de las notas (`sum`) entre el número total de estudiantes (`count`). Esto nos da el promedio de las notas.

## 7. Combina lo Aprendido: Crear Listados

Vamos a juntar algunos de estos conceptos en un ejemplo más elaborado.

**Ejemplo 12: Crear un listado de nombres**
```bash
echo -e "Alice:1234\nBob:5678\nCharlie:91011" > contactos.txt
cut -d ':' -f1 contactos.txt | sort
```

<details><summary>🏃 How to Run</summary>

**1. Crear el archivo `contactos.sh`:**
   * Para crear el archivo `contactos.sh`, abre la terminal en Replit y escribe:
   ```bash
   code contactos.sh
   ```
   * Esto abrirá el editor de texto. En él, escribe el siguiente código:

   ```bash
   echo -e "Alice:1234\nBob:5678\nCharlie:91011" > contactos.txt
   cut -d ':' -f1 contactos.txt | sort
   ```

**2. Cambiar los permisos:**
   * En la terminal, ejecuta el siguiente comando para otorgar permisos de ejecución al archivo:

   ```bash
   chmod +x contactos.sh
   ```

**3. Ejecutar el script:**
   * Ahora puedes ejecutar el script como un comando:

   ```bash
   ./contactos.sh
   ```

**4. Ver el resultado:**
   * Al ejecutar el script, se creará un archivo llamado `contactos.txt` con una lista de nombres y números de teléfono, separados por dos puntos. Luego, el comando `cut -d ':' -f1 contactos.txt` extraerá la primera parte de cada línea (los nombres), y `sort` ordenará esos nombres alfabéticamente. El resultado se mostrará en la terminal.

</details>

**Qué sucede:**
- `cut -d ':' -f1 contactos.txt` extrae los nombres de los contactos.
- `sort` ordena los nombres alfabéticamente.

Este ejemplo demuestra cómo puedes combinar `cut` y `sort` para manipular y organizar datos.

## Conclusión

Estos comandos son herramientas esenciales en tu caja de herramientas de `bash`. Aunque hemos usado ejemplos simples, estos conceptos son aplicables en scripts mucho más complejos.

Aquí tienes la presentación del código junto con el "how to run" y el "qué sucede":

---

**Ejemplo 13: Manejo de un Banco con Bash**

Este script de Bash proporciona una solución para gestionar una pequeña base de datos de clientes de un banco, permitiendo agregar, borrar, consultar, consignar y retirar dinero, así como generar un reporte. 

El script utiliza un archivo llamado `banco.txt` para almacenar la información de los clientes y sus saldos. Los clientes pueden interactuar con el sistema mediante un menú que ofrece varias opciones para realizar diferentes operaciones.

```bash
#!/bin/bash

BANCO="banco.txt"

# Función para mostrar el menú
mostrar_menu() {
    echo "----------------------------------"
    echo "            Banco                 "
    echo "----------------------------------"
    echo "1. Agregar cliente"
    echo "2. Borrar cliente"
    echo "3. Consultar saldo de cliente"
    echo "4. Listar clientes"    # Nueva opción
    echo "5. Consignar"
    echo "6. Retirar"
    echo "7. Total de saldos"
    echo "8. Generar reporte"
    echo "0. Salir"
    echo "----------------------------------"
    echo -n "Selecciona una opción: "
}

# Función para agregar un cliente
agregar_cliente() {
    echo -n "Ingrese el nombre del cliente: "
    read nombre
    # Comprobar si el archivo existe y crearlo si no es así
    if [ ! -f "$BANCO" ]; then
        touch "$BANCO"
        echo "Se ha creado el archivo $BANCO"
    fi
    if grep -q "^$nombre:" "$BANCO"; then
        echo "El cliente ya existe."
    else
        echo -n "Ingrese el saldo inicial: "
        read saldo
        echo "$nombre:$saldo" >> "$BANCO"
        echo "Cliente agregado con éxito."
    fi
}

# Función para borrar un cliente
borrar_cliente() {
    echo -n "Ingrese el nombre del cliente a borrar: "
    read nombre
    sed -i "/^$nombre:/d" "$BANCO"
    echo "Cliente borrado, si existía."
}

# Función para consultar el saldo de un cliente
consultar_saldo() {
    echo -n "Ingrese el nombre del cliente: "
    read nombre
    saldo=$(grep "^$nombre:" "$BANCO" | cut -d ':' -f2)
    if [ -z "$saldo" ]; then
        echo "Cliente no encontrado."
    else
        echo "El saldo de $nombre es: $saldo"
    fi
}

# Función para listar los clientes
listar_clientes() {
    echo "Lista de clientes:"
    echo "╔═══════════════╦════════════╗"
    echo "║ Nombre        ║ Saldo      ║"
    echo "╠═══════════════╬════════════╣"
    awk -F: '{printf "║ %-13s ║ %10d ║\n", $1, $2}' "$BANCO" | sort
    echo "╚═══════════════╩════════════╝"
}

# Función para consignar dinero a un cliente
consignar() {
    echo -n "Ingrese el nombre del cliente: "
    read nombre
    echo -n "Ingrese la cantidad a consignar: "
    read cantidad
    if grep -q "^$nombre:" "$BANCO"; then
        saldo_actual=$(grep "^$nombre:" "$BANCO" | cut -d ':' -f2)
        nuevo_saldo=$((saldo_actual + cantidad))
        sed -i "s/^$nombre:.*/$nombre:$nuevo_saldo/" "$BANCO"
        echo "Consignación realizada. El nuevo saldo es: $nuevo_saldo"
    else
        echo "Cliente no encontrado."
    fi
}

# Función para retirar dinero de un cliente
retirar() {
    echo -n "Ingrese el nombre del cliente: "
    read nombre
    echo -n "Ingrese la cantidad a retirar: "
    read cantidad
    if grep -q "^$nombre:" "$BANCO"; then
        saldo_actual=$(grep "^$nombre:" "$BANCO" | cut -d ':' -f2)
        if [ "$cantidad" -le "$saldo_actual" ]; then
            nuevo_saldo=$((saldo_actual - cantidad))
            sed -i "s/^$nombre:.*/$nombre:$nuevo_saldo/" "$BANCO"
            echo "Retiro realizado. El nuevo saldo es: $nuevo_saldo"
        else
            echo "Saldo insuficiente."
        fi
    else
        echo "Cliente no encontrado."
    fi
}

# Función para mostrar el total de saldos de todos los clientes
total_saldos() {
    total=0
    while IFS=":" read -r nombre saldo; do
        total=$((total + saldo))
    done < "$BANCO"
    echo "El total de saldos es: $total"
}

# Función para generar un reporte ordenado por nombre con total de saldos
generar_reporte() {
    sort -t ':' -k1,1 "$BANCO" > reporte.txt 
    total=0
    while IFS=":" read -r nombre saldo; do
        total=$((total + saldo))
    done < "$BANCO"
    echo "----------------------" >> reporte.txt
    echo "Total de saldos: $total" >> reporte.txt
    echo "Reporte generado en 'reporte.txt'"
}

generar_reporte2() {
  total=0
  echo "╔═══════════════╦════════════╦═════════════════╗" > reporte.txt
  echo "║ Nombre        ║ Saldo      ║ Total Acumulado ║" >> reporte.txt
  echo "╠═══════════════╬════════════╬═════════════════╣" >> reporte.txt
  awk -F: '{printf "║ %-13s ║ %10d ║ %15d ║\n", $1, $2, total+= $2}' "$BANCO" | sort -t ':' -k1,1 >> reporte.txt
  echo "╚═══════════════╩════════════╩═════════════════╝" >> reporte.txt
  echo "Reporte generado en 'reporte.txt'"
}

# Bucle principal
while true; do
    mostrar_menu
    read opcion
    case $opcion in
        1) agregar_cliente ;;
        2) borrar_cliente ;;
        3) consultar_saldo ;;
        4) listar_clientes ;;   
        5) consignar ;;
        6) retirar ;;
        7) total_saldos ;;
        8) generar_reporte2 ;;
        0) echo "Saliendo..."; exit 0 ;;
        *) echo "Opción no válida, intenta de nuevo." ;;
    esac
done
```

<details><summary>🏃 How to Run</summary>

**1. Crear el archivo `banco.sh`:**
   * Para crear el archivo `banco.sh`, abre la terminal en Replit y escribe:
   ```bash
   code banco.sh
   ```
   * Esto abrirá el editor de texto. En él, escribe el siguiente código:

   ```bash
   #!/bin/bash

   BANCO="banco.txt"
   # (Agrega aquí el resto del código del script)
   ```

**2. Cambiar los permisos:**
   * En la terminal, ejecuta el siguiente comando para otorgar permisos de ejecución al archivo:

   ```bash
   chmod +x banco.sh
   ```

**3. Ejecutar el script:**
   * Ahora puedes ejecutar el script como un comando:

   ```bash
   ./banco.sh
   ```

**4. Interactuar con el script:**
   * Al ejecutar el script, verás un menú con opciones para gestionar los clientes y sus saldos. Selecciona la opción deseada e ingresa los datos requeridos según la opción que elijas.

</details>

**Qué sucede:**

### 1. `#!/bin/bash`
- Indica que el script debe ser ejecutado con el intérprete de Bash.

### 2. `BANCO="banco.txt"`
- Define la variable `BANCO` que contiene el nombre del archivo donde se almacenan los datos de los clientes.

### 3. `mostrar_menu`
- Función que muestra el menú de opciones disponibles en el script.

### 4. `agregar_cliente`
- **`grep -q "^$nombre:" "$BANCO"`**
  - **`grep`**: Busca líneas en un archivo que coincidan con un patrón.
  - **`-q`**: Modo silencioso. Suprime la salida del contenido que coincide, solo devuelve el código de salida.
  - **`"^$nombre:"`**: Expresión regular que busca líneas que comienzan (`^`) con el valor de la variable `$nombre` seguido de un `:`.

- **`echo "$nombre:$saldo" >> "$BANCO"`**
  - **`echo`**: Imprime texto en la salida estándar.
  - **`"$nombre:$saldo"`**: Formato del texto a añadir, que incluye el nombre del cliente y su saldo.
  - **`>> "$BANCO"`**: Redirige la salida para agregar el texto al final del archivo `BANCO`.

### 5. `borrar_cliente`
- **`sed -i "/^$nombre:/d" "$BANCO"`**
  - **`sed`**: Editor de flujo para modificar archivos de texto.
  - **`-i`**: Edita el archivo en el lugar, sin necesidad de crear un archivo temporal.
  - **`"/^$nombre:/d"`**: Expresión que elimina cualquier línea que comience con `$nombre` seguido de `:`.

### 6. `consultar_saldo`
- **`grep "^$nombre:" "$BANCO"`**
  - **`grep`**: Busca líneas en un archivo que coincidan con un patrón.
  - **`"^$nombre:"`**: Expresión regular que busca líneas que comienzan (`^`) con el valor de `$nombre` seguido de `:`.

- **`cut -d ':' -f2`**
  - **`cut`**: Extrae secciones de cada línea de un archivo.
  - **`-d ':'`**: Define `:` como el delimitador de campos en la línea.
  - **`-f2`**: Extrae el segundo campo, que es el saldo del cliente en la línea.

### 7. `consignar`
- **`sed -i "s/^$nombre:.*/$nombre:$nuevo_saldo/" "$BANCO"`**
  - **`sed`**: Editor de flujo para modificar archivos de texto.
  - **`-i`**: Edita el archivo en el lugar, sin necesidad de crear un archivo temporal.
  - **`"s/^$nombre:.*/$nombre:$nuevo_saldo/"`**: Comando de sustitución que busca una línea que comience con `$nombre` y reemplaza el resto de la línea con `$nombre:$nuevo_saldo`.

### 8. `retirar`
- **`sed -i "s/^$nombre:.*/$nombre:$nuevo_saldo/" "$BANCO"`**
  - **`sed`**: Editor de flujo para modificar archivos de texto.
  - **`-i`**: Edita el archivo en el lugar, sin necesidad de crear un archivo temporal.
  - **`"s/^$nombre:.*/$nombre:$nuevo_saldo/"`**: Similar al comando en `consignar`, reemplaza la línea que comienza con `$nombre` con una línea actualizada que muestra el saldo después del retiro.

### 9. `total_saldos`
- **`while IFS=":" read -r nombre saldo; do ... done < "$BANCO"`**
  - **`while`**: Ejecuta un bucle mientras la condición sea verdadera.
  - **`IFS=":"`**: Variable de separador de campo. Define `:` como el delimitador para dividir cada línea en campos.
  - **`read -r nombre saldo`**: Lee una línea del archivo `BANCO`, asignando el primer campo a `nombre` y el segundo campo a `saldo`.
  - **`total=$((total + saldo))`**: Acumula el saldo de cada cliente en la variable `total`.
  - **`done < "$BANCO"`**: Redirige el archivo `BANCO` como entrada al bucle `while`.

### 10. `generar_reporte`
- **`sort -t ':' -k1,1 "$BANCO" > reporte.txt`**
  - **`sort`**: Ordena líneas de texto en un archivo.
  - **`-t ':'`**: Define `:` como el delimitador de campos para la ordenación.
  - **`-k1,1`**: Ordena las líneas utilizando solo el primer campo (nombre del cliente) como clave de ordenación.
  - **`> reporte.txt`**: Redirige la salida del comando `sort` a un archivo llamado `reporte.txt`.

- **`awk -F: '{printf "║ %-13s ║ %10d ║\n", $1, $2}' "$BANCO" | sort >> reporte.txt`**
  - **`awk -F:`**: Usa `:` como delimitador y formatea la salida en una tabla con nombre (`$1`) y saldo (`$2`) de cada cliente.
  - **`sort`**: Ordena las líneas del archivo `BANCO` alfabéticamente por nombre antes de agregarlo a `reporte.txt`.

### 11. `listar_clientes`
- **`awk -F: '{print $1}' "$BANCO" | sort`**
  - **`awk -F:`**: Usa `:` como delimitador para separar campos.
  - **`'{print $1}'`**: Imprime el primer campo de cada línea (nombre del cliente).
  - **`sort`**: Ordena alfabéticamente los nombres de los clientes.

### 12. `while true; do ... done`
- **`while`**: Ejecuta un bucle mientras la condición sea verdadera.
- **`true`**: Condición que siempre es verdadera, por lo que el bucle `while` se ejecuta indefinidamente.
- **`do ... done`**: Cuerpo del bucle que ejecuta el código entre `do` y `done`.
---

&nbsp;

<p align="center">
  <img src="img/taller.png" height="60">
</p>

# Taller de Agenda Telefónica

Ahora que has visto cómo funciona un sistema de gestión de banco con `bash`, te invitamos a aplicar estos conceptos para resolver un nuevo problema. Imagina una **agenda telefónica** que debe permitir gestionar contactos y teléfonos. Deberás crear un menú similar al del script del banco que permita:

1. **Agregar contacto:** Añadir un nuevo contacto a la agenda.
2. **Consultar contacto:** Buscar y mostrar el número de teléfono de un contacto específico.
3. **Borrar contacto:** Eliminar un contacto de la agenda.
4. **Listar contactos:** Mostrar todos los contactos almacenados.
5. **Ordenar por nombre:** Organizar los contactos alfabéticamente por nombre.
6. **Ordenar por teléfono:** Organizar los contactos por número de teléfono.
7. **Generar reporte:** Crear un archivo con una lista ordenada de contactos.

Este ejercicio te permitirá reforzar tus habilidades en scripting y te ayudará a ver cómo se aplican en situaciones prácticas. ¡Buena suerte y disfruta del desafío!

---