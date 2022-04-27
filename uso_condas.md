# CONDA

## Comandos:

- Mostrar ambientes creados

`conda env list`

Por default conda instala el ambiente base

- Crear ambiente

`conda create --name py35 python=3.5 pandas`

> Lo llamamos py35 porque instalamos el paquete pyrhon v 3.5, también agregamos pandas (si no ponemos version instala la más reciente para la version de python instalada)

- Para activar el ambiente

`conda activate py35`

- Para desactivar el ambiente

`conda deactivate`

- Para ver los paquetes / versiones instalados en el ambiente

`conda list`

- Ver version puntual de un paquete

`conda list pandas`

- Actualizar paquete

`conda update pandas`

- Instalar la version más reciente

`conda install python=3.9 pandas`

- Cambiar nombre al ambiente

`conda create --name py39 --copy --clone py35`

- Eliminar un paquete del ambiente

`conda remove pandas`

- Eliminar el ambiente

`conda env remove --name py35`

- Creamos ambiente

`conda create --name py39 python=3.9 pandas=1.2`

- Intentamos instalar paquete boltons

`conda install boltons`

--> PackagesNotFoundError: The following packages are not available from current channels:

- boltons

Current channels:

- https://repo.anaconda.com/pkgs/main/linux-64
- https://repo.anaconda.com/pkgs/main/noarch
- https://repo.anaconda.com/pkgs/r/linux-64
- https://repo.anaconda.com/pkgs/r/noarch

To search for alternate channels that may provide the conda package you're
looking for, navigate to

    https://anaconda.org

and use the search bar at the top of the page.

- Navegamos a https://anaconda.org y buscamos boltons y buscamos en que canal se encuentra

- Instalamos el canal y el paquete

`conda install --channel conda-forge boltons`

- Listar las revisiones. Nos indica qué instalamos

`conda list --revision`

- Vover a una revision anterior. Debemos indicar el nro

`conda install --revision 0`

- Exportar un ambiente para compartirlo

`conda env export`

- Elimina algunos comentarios, lo genera con paquete / version

`conda env export --no-builds`

- El mejor. Lo genera solo con los paquetes que ingresamos manulamente. No incluye las dependencias

`conda env export --from-history`

- Lo incluimos en un archivo

`conda env export --from-history --file environment.yml`

- Simularemos que somos otra px para instalarlo

```
conda deactivate
conda env remove --name py39
conda env create --file environment.yml
```

---

## MAMBA -> Conda optimizado

---

- Instalación

```
conda
conda install --channel conda-forge mamba
```

- Ayuda

`mamba --help`

- Eliminamos el ambiente anterior para reinstalarlo con mamba

```
conda deactivate
conda env remove --name py39
mamba env create --file environment.yml
```
