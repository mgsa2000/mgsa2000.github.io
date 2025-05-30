# practica-6.1

 En esta práctica llevaremos a cabo la creación y configuración de un sitios web estático MkDocs y lo publicaremos en GitHub Pages

 ## pasos panteriores

 tener una máquina en aws con docker instalado.

 ## 1. Instalación
 Una vez dentro de nuestra máquina ejecutamos el siguiente comando para ejecutar un nuevo proyecto docker run --rm -it -p 8000:8000 -u $(id -u):$(id -g) -v "$PWD":/docs squidfunk/mkdocs-material new .

 ![](imagenes/111.png)


 El comando anterior creará el archivo de configuración mkdocs.yml y el archivo Markdown index.md dentro del directorio docs.

.
└── proyecto
    ├── docs
    │   └── index.md
    └── mkdocs.yml

## 2. configuración de mkdocs.yml
Una vez hayamos creado el archivo mkdocs,lo editaremos para configurar nuestro sitio web,


````
site_name: Miguel IAW
nav:
    - Principal: index.md
    - Practica 3.1: practica-3.1.md
    - Practica 4.5: practica-4.5.md

theme:
  name: material  

  palette:
    # Modo claro
    - scheme: default
      primary: teal
      accent: black
      toggle:
        icon: material/toggle-switch
        name: Switch to dark mode

    # Modo oscuro
    - scheme: slate
      primary: teal
      accent: black
      toggle:
        icon: material/toggle-switch-off-outline
        name: Switch to light mode

  features:
    - header.autohide
    - navigation.footer

extra:
  language: eu
  social:
    - icon: fontawesome/brands/github 
      link: https://github.com/mgsa2000
    - icon: fontawesome/brands/docker
      link: https://hub.docker.com/u/stratachan3




plugins:
  - offline

copyright: Copyright - 2025 Miguel strachan

````

aqui configuramos lo siguiente;

1-Nombre del sitioweb y menú de navegación.
2-Definimos que el color principal del tema sea teal(verde azulado), color de acento negro y además creamos la opción de que mediante un botón podamos poner la página en modo claro o oscuro.

3-Establecemos la opcion de que la barra superior se oculte al scrolear hacia abajo y que se muestren botones de navegación en el pié de página.
4- Ponemos el sitio en español y ponemos dos iconos que nos lleve a nuestra página de github y a docker hub.

5-añadimos el plugging con que el que podremos navegar por la documentacion sin conexión y un mensaje de Copyright en el pie de página.



Para previsualizar como quedaría el sitio web, podemos ejecutar el siguiente comando

docker run --rm -it -p 8000:8000 -u $(id -u):$(id -g) -v "$PWD":/docs squidfunk/mkdocs-material

Y para visualizarlos abriremos un navegador e introduciremos la siguiente dirección http://localhost:8000


![](imagenes/222.png)

## generar la documentación
Para generar los archivos HTML estaticos ejecutamos  
docker run --rm -it -u $(id -u):$(id -g) -v "$PWD":/docs squidfunk/mkdocs-material build