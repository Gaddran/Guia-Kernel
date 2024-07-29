<div>
<img src="https://i.ibb.co/v3CvVz9/udd-short.png" width="150"/>
    <br>
    <strong>Universidad del Desarrollo</strong><br>
    <em>Magíster en Data Science</em><br>
    <em>Profesor: Víctor Navarro Aránguiz</em><br>
    <em>Autor: Giuseppe Lavarello</em><br>
</div>

# Python para Data Science: Repaso grupal 

**Fecha de repaso**: 28 de Julio de 2024

# Objetivos:
- Desenredar el uso de conda y la creación de entornos y kernels vistos en la clase pasada.

# Usos de un Entorno de Conda

### 1. **Aislamiento de Proyectos**
   - **Descripción**: Cada entorno de Conda puede tener su propia versión de Python y paquetes instalados. Esto evita conflictos entre proyectos que requieren diferentes versiones de bibliotecas.
   - **Ejemplo**: Puedes tener un entorno para un proyecto que usa `numpy` 1.18 y otro entorno para un proyecto que usa `numpy` 1.21.

### 2. **Gestión de Dependencias**
   - **Descripción**: Los entornos permiten gestionar las dependencias específicas de cada proyecto. Puedes instalar, actualizar y eliminar paquetes sin afectar otros proyectos.
   - **Ejemplo**: Instalar `scikit-learn` en un entorno y mantener otras versiones o paquetes distintos en otros entornos.

### 3. **Reproducibilidad de Experimentos**
   - **Descripción**: Crear un entorno con las versiones exactas de paquetes y Python asegura que el código se ejecute de manera consistente en diferentes máquinas o entornos.
   - **Ejemplo**: Exportar un archivo `environment.yml` con las especificaciones del entorno para reproducir el entorno en otra máquina.

### 4. **Pruebas de Compatibilidad**
   - **Descripción**: Puedes probar tu código con diferentes versiones de bibliotecas o Python sin comprometer la estabilidad de tu entorno principal.
   - **Ejemplo**: Crear un entorno para probar la compatibilidad con una nueva versión de una biblioteca antes de actualizarla en el entorno de producción.

### 5. **Entornos de Desarrollo y Producción**
   - **Descripción**: Puedes crear entornos separados para el desarrollo y la producción de tu aplicación. Esto asegura que las dependencias de desarrollo no interfieran con el entorno de producción.
   - **Ejemplo**: Un entorno de desarrollo puede incluir herramientas de depuración y documentación, mientras que el entorno de producción solo incluye las dependencias necesarias para ejecutar la aplicación.

### 6. **Gestión de Paquetes con Conda y Pip**
   - **Descripción**: Conda permite instalar paquetes tanto desde sus repositorios como desde PyPI (Python Package Index) usando `pip`, facilitando la instalación de paquetes que no están disponibles en Conda.
   - **Ejemplo**: Instalar paquetes de Conda y luego usar `pip` para instalar una biblioteca adicional no disponible en Conda.

### 7. **Facilitar la Colaboración**
   - **Descripción**: Compartir entornos con colaboradores usando un archivo `environment.yml` permite a otros usuarios replicar exactamente el entorno necesario para trabajar en un proyecto.
   - **Ejemplo**: Crear un archivo `environment.yml` que otros colaboradores pueden usar para crear un entorno idéntico con `conda env create -f environment.yml`.

### 8. **Manejo de Versiones de Python**
   - **Descripción**: Permite gestionar múltiples versiones de Python y sus paquetes sin conflictos. Esto es útil si trabajas con proyectos que requieren diferentes versiones de Python.
   - **Ejemplo**: Tener un entorno con Python 3.8 para un proyecto y otro con Python 3.9 para otro proyecto.



# Cómo Crear un Entorno con Conda

### Prerequisito: Instalar Conda
1. **Descargar e Instalar Miniconda o Anaconda**:
   - **Miniconda**: Visita [miniconda.org](https://docs.conda.io/en/latest/miniconda.html) para descargar e instalar Miniconda.
   - **Anaconda**: Visita [anaconda.com](https://www.anaconda.com/products/distribution) para descargar e instalar Anaconda, que incluye Conda y muchas bibliotecas científicas preinstaladas.

### Paso 1: Abrir la Terminal o Anaconda Prompt
1. **En Windows**: Abre **Anaconda Prompt** desde el menú de inicio.  
![alt text](.\\Imagenes\\abrir_prompt.png)
2. **En macOS/Linux**: Abre la **Terminal**.

### Paso 2: Crear un Nuevo Entorno
1. Ejecuta el siguiente comando para crear un nuevo entorno (reemplaza `myenv` con el nombre que deseas darle al entorno y `python=3.12` con la versión de Python que prefieras):
   ```sh
   conda create --name myenv python=3.12
   ```
# Cómo Utilizar un Entorno con Conda

### Activar el Entorno
- Para activar el entorno que acabas de crear, usa el siguiente comando:

    ```sh
    conda activate myenv
    ```
- Verificar el Entorno Activo: El nombre del entorno debería aparecer en la línea de comandos, indicando que el entorno está activo.

### Instalar Paquetes Adicionales en el Entorno
- Para instalar paquetes adicionales en el entorno activo, usa el comando:
    ```sh
    conda install nombre_del_paquete
    ```
- Por ejemplo, para instalar matplotlib:
    ```sh
    conda install matplotlib
    ```
###  Desactivar el Entorno
- Para desactivar el entorno y volver al entorno base, usa el comando:
    ```sh
    conda deactivate
    ```
###  Eliminar un Entorno
- Si deseas eliminar un entorno que ya no necesitas, asegúrate de que el entorno **no esté activo** y ejecuta:
    ```sh
    conda remove --name myenv --all
    ```
# Cómo Crear un Kernel con Conda para Jupyter

Para crear un kernel con Conda para usarlo en Jupyter Notebook, sigue estos pasos:

### Paso 1: Instalar Jupyter Notebook

1. **Activar el Entorno**:
   - Abre la terminal o Anaconda Prompt.  
   - Activa el entorno en el que deseas instalar Jupyter Notebook:  

     ```sh
     conda activate myenv
     ```
    ![check_env.jpg](.\\Imagenes\\check_env.jpg)

2. **Instalar Jupyter Notebook**:
   - Como Jupyter Notebook no debería estar instalado en el entorno, instálalo con:
     ```sh
     conda install jupyter
     ```
    ![instalar_jupyter_01](.\\Imagenes\\instalar_jupyter_01.jpg) 
    ![instalar_jupyter_02](.\\Imagenes\\instalar_jupyter_02.jpg)     


### Paso 2: Instalar el Paquete `ipykernel`

1. **Instalar `ipykernel`** (opcional, instalar jupyter deberia haberlo instalado):
   - Asegúrate de que el entorno esté activado y luego instala `ipykernel`:
     ```sh
     conda install ipykernel
     ```
    ![installar_kernel](.\\Imagenes\\installar_kernel.jpg)  

### Paso 3: Crear el Kernel

1. **Registrar el Kernel**:
   - Ejecuta el siguiente comando para crear un kernel con un nombre específico (reemplaza `myenv` con el nombre de tu entorno y `myenv-kernel` con el nombre del kernel que deseas):
     ```sh
     python -m ipykernel install --user --name myenv --display-name "myenv-kernel"
     ```
    ![crear_kernel](.\\Imagenes\\crear_kernel.jpg)  

   - **Explicación de los parámetros**:
     - `--name myenv`: El nombre del kernel (debe coincidir con el nombre del entorno de Conda).
     - `--display-name "myenv-kernel"`: El nombre que aparecerá en el menú de selección de kernel en Jupyter Notebook.

### Paso 4: Verificar el Kernel en Jupyter Notebook

1. **Iniciar Jupyter Notebook**:
   - Ejecuta el siguiente comando para iniciar Jupyter Notebook:
     ```sh
     jupyter notebook
     ```

2. **Seleccionar el Kernel**:
   - Abre un nuevo cuaderno (notebook) en Jupyter.
   - En el menú **Kernel** > **Change kernel**, deberías ver el kernel que creaste, por ejemplo, **myenv-kernel**.
   - Selecciona el kernel para usar el entorno Conda específico en tu cuaderno.

### Paso 5: Eliminar un Kernel (Opcional)
1. **Listar los Kernels existentes**:
     ```sh
     jupyter kernelspec list
     ```
2. **Eliminar el Kernel**:
   - Si deseas eliminar un kernel, ejecuta:
     ```sh
     jupyter kernelspec uninstall myenv-kernel
     ```
   - Reemplaza `myenv-kernel` con el nombre del kernel que deseas eliminar.

