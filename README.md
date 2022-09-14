
# Instalación de IRAF en Ubuntu/Debian Linux (Versión no soportada)

---

## 1. Introducción

Aquí se indica la instalación de IRAF en su versión ahora no soportada, para Ubuntu/Debian en arquitecturas de 64-bit.
Se incluye la activación de la herramienta de visualización DS9.

Esta instalación está dirigida a quienes por alguna razón necesita o prefieren el trabajo en las versión inicial. Para la versión actual diríjase a https://iraf-community.github.io/pyraf.html

La instalación se realizará a través de lineas de comando en terminal. 

Esta es una versión basada en la presentada por Rubab Khan (khan@astronomy.ohio-state.edu)

## 2. Instalación IRAF
### 2.1 Descargas

En su carpeta Descargas (Downloads) descargue el archivo [IRAF_VersinClsica.tar.xz](https://1drv.ms/u/s!AnFDFXokQzgljB0-3E8e2sM1hAJW). Este archivo comprimido contiene los archivos: ***iraf.lnux.x86_64.tar.gz***, ***x11iraf-v2.0BETA-bin.linux.tar.gz***, ***exercises.tar.xz*** e ***iraf***.

Para descomprimir desde terminal el archivo ***IRAF_VersinClsica.tar.xz*** en la carpeta Descargas (Downloads), inicie abriendo la terminal tecleando: 

```
Ctrl + Alt + T
```
en la terminal copie y pegue las siguientes dos instrucciones (debe tener instalado el descopresor, pude hacerlo pegando en la terminal  ` sudo apt-get install tar`)

```
cd Descargas
tar -xf IRAF_VersinClsica.tar.xz
```

no cierre la terminal.

### 2.2 Instalación iraf

En esta misma terminal (la anteriormente abierta) actualice las librerias que usa IRAF, copie y pegue la siguiente instrucción que actualizará e instalará dichas librerías :

```
cd
sudo apt-get install tcsh libxss1 lib32z1 lib32ncurses6 libbz2-1.0:i386 libxmu6:i386
sudo apt-get install libxmu6:i386
sudo apt-get install libncurses5:i386
sudo apt-get install libncurses5
```  
De en la terminal de la instrucción `Y` y lugeo la tecla *Enter*. Ahora, en la misma terminal pegue la siguiente instrucción que crea una carpeta con el nombre *iraf* (esta se crea en el Directorio Raíz o directorio "/"):

```
sudo mkdir /Iraf
```
En la carpeta *Iraf* se crearán dos nuevas carpeta con los nombres *iraf* y *x11iraf* (en minúscula la letra inicial)

```
sudo mkdir /Iraf/iraf 
sudo mkdir /Iraf/x11iraf

```
Ahora lleve el archivo ***iraf.lnux.x86_64.tar.gz*** a la carpeta *iraf* y el archivo ***x11iraf-v2.0BETA-bin.linux.tar.gz*** a la carpeta *x11iraf* respectivamente. Para lo anterior, (en la misma terminal) ingresamos a la carpeta *Descargas* (*Downloads*) con la instrucción 

```
cd Descargas
```
y luego 

```
cd IRAF_VersinClsica
sudo mv iraf.lnux.x86_64.tar.gz /Iraf/iraf/.
sudo mv x11iraf-v2.0BETA-bin.linux.tar.gz /Iraf/x11iraf/.
```

Ahora se debe descomprimir cada archivo (***.tar.gz***) en su respectiva carpeta, para lo cual se debe dirigir al Directorio Raíz con la siguiente instrucción (continuamos en la misma terminal)

```
cd /
```


* Inicie en la capeta ***iraf***, por tanto en la misma terminal:

  ```
  cd Iraf/iraf
  ```

  Descomprima:
  ```
  sudo tar -xf iraf.lnux.x86_64.tar.gz
  ```
  Resultados de la descompresión aparecerán el ejecutables *Install*, realice la instalación: 

  ```
  sudo ./install
  ```
  en esta última instrucción indique a la terminal que debe continuar escribiendo *yes* (o solamente *y*), luego use la tecla *Enter*.

  Entre otras, irán apareciendo en su orden las siguientes instrucciones, a las cuales debe ir tecleando *Enter*:
  ```
  New iraf root directory (/iraf/iraf): 
  Default root image storage directory (/iraf/imdirs): 
  Default root cache directory (/iraf/cache): 
  Local unix commands directory (/usr/local/bin): 
  ```
  Una vez finalizado este proceso aparecerá:

  ```
  ========================================================================
  ================  Installation Completed With No Errors  ===============
  ========================================================================
  ```

* Continúe de manera similar a lo anterior, ingresando a la carpeta ***x11iraf***:

  ```
  cd ..
  cd x11iraf
  sudo tar -xf x11iraf-v2.0BETA-bin.linux.tar.gz
  sudo ./install
  ```

  Y nuevamente presionamos la tecla *Enter* hasta que complete la instalación.

No cierre la terminal.

## 3. Instalación del visor ds9

Ahora, instalaremos el visor de imágenes **ds9**.

Siga el link [saoimageds9](https://sites.google.com/cfa.harvard.edu/saoimageds9), descargue en la carpeta *Descargas* (Downloads) el archivo ***ds9.ubuntu20.8.3.tar.gz*** (descargue una versión reciente para linux).

Ahora regrese a la carpeta *Descargas* (continúe en la misma terminal) y descomprima el archivo:
```
cd
cd Descargas
tar -xf ds9.ubuntu20.8.3.tar.gz
```
y lleve el elemento ***ds9*** resultado de la descompresión a la carpeta *bin*:

```
sudo mv ds9 /usr/local/bin/.
```

## 4. Script para iniciar Iraf y ds9

Primero cree la carpeta *IRAF* (aquí se alojará la carpeta de parámetros del las taraes de Iraf *uparm*):
```
cd
mkdir IRAF
cd IRAF
```
Ahora, se creará la carpeta de parámetros de las tareas de Iraf con la instrucción: 

```
mkiraf
```

y damos *Enter* para indicar que el tipo de terminal a usar es *xgterm*.


Luego, desde la carpeta Descargas (Downloads) se moverá el script *iraf* a ***Home****, con la siguiente instrucción

```
cd
cd Descargas/IRAF_VersinClsica/
sudo mv iraf ~/
```
Ahora, se hará ejecutable el script de ***home***
```
cd
sudo chmod u=rwx iraf

```
Finalmente, cierre la terminal.

## 5. Inicie Iraf

Abra una nueva terminal 

```
Ctrl + Alt + T
```
escriba en esta terminal

```
./iraf
```
y tecleé *Enter*. Esta instrucción le abrirá Iraf en una terminal tipo xgterm y el visor DS9.

## 6. Comentarios

Si presenta problemas con los paquetes de 32 bits que usa IRAF, es posible que se deba al cambio de nombre del paquete por las versiones más actuales (por ejemplo de *libncurses5* a *lib32ncurses6* ). 
La recomendación es hacer una consulta del nombre del paquete actualizado y reemplazar en las lineas donde se instalan los paquetes.
