Descripción
Esta es una API construida con Node.js y Express que se conecta a una base de datos MySQL utilizando mysql2 y sequelize. Esta API proporciona una estructura básica para el desarrollo y administración de una base de datos.

Instalación
Descargar el proyecto

Clona o descarga el proyecto desde el repositorio.

Instalar las dependencias

Navega a la carpeta del proyecto y ejecuta el siguiente comando para instalar las dependencias:

bash
Copy code
npm install
Esto instalará todas las dependencias listadas en package.json.

Configurar la base de datos

Dentro de la carpeta api/conexion, encontrarás un archivo SQL llamado examenisc.sql. Utiliza este archivo para crear la base de datos.
Antes de ejecutar el script SQL, asegúrate de crear una base de datos con el nombre examen en tu servidor local (por ejemplo, XAMPP).
Configurar el archivo .env

Dentro del archivo  .env ubicado en la raíz del proyecto.

Configura las variables de entorno necesarias, como el puerto, la contraseña y el usuario para tu base de datos local. Un ejemplo de configuración puede ser:

DB_NAME=examen
DB_USER=root
DB_PASSWORD= 
DB_HOST=localhost
DB_DIALECT=mysql   
DB_PORT=3306
Ejecución

Para iniciar el proyecto, ejecuta el siguiente comando en la terminal:

bash
Copy code
node index.js
Esto iniciará el servidor Express en el puerto especificado en el archivo ubicado en ./Servidor/Servidor.js que sera el puerto 3000

Scripts
test: Actualmente, no se han definido pruebas para este proyecto. Puedes modificar este script en el archivo package.json según sea necesario.
Dependencias
cors: ^2.8.5
dotenv: ^16.4.5
express: ^4.20.0
jsonwebtoken: ^9.0.2
mysql2: ^3.11.1
sequelize: ^6.37.3


/*Carpeta examen*/

Descripción
Este es un proyecto frontend basado en Vue 3, utilizando Vite como bundler y varios componentes de UI y librerías para una experiencia moderna de desarrollo web. El proyecto incluye soporte para Bootstrap.

Instalación
Descargar el proyecto

Clona o descarga el proyecto desde el repositorio.

Instalar las dependencias

Navega a la carpeta del proyecto y ejecuta el siguiente comando para instalar todas las dependencias:

bash
Copy code
npm install
Esto instalará las dependencias listadas en package.json.

Scripts
El proyecto incluye los siguientes scripts para facilitar el desarrollo y la construcción:

dev: Inicia el servidor de desarrollo utilizando Vite.

bash
Copy code
npm run dev
build: Construye el proyecto para producción, generando los archivos optimizados en la carpeta dist.

bash
Copy code
npm run build
preview: Previsualiza la aplicación construida en modo producción.

bash
Copy code
npm run preview
Dependencias
Dependencias principales
@fortawesome/fontawesome-free: ^6.6.0
@fortawesome/fontawesome-svg-core: ^6.6.0
@fortawesome/free-solid-svg-icons: ^6.6.0
@fortawesome/vue-fontawesome: ^3.0.8
@mdi/font: ^7.4.47
axios: ^1.7.7
bootstrap: ^5.3.3
vue: ^3.4.37
vue-router: ^4.4.3
Dependencias de desarrollo
@vitejs/plugin-vue: ^5.1.2
autoprefixer: ^10.4.20
postcss: ^8.4.45
vite: ^5.4.1
Configuración
El proyecto utiliza varios frameworks y librerías de diseño, por lo que es posible que necesites ajustar la configuración de tu entorno de desarrollo para integrarlos adecuadamente. Asegúrate de seguir la documentación oficial de cada librería para personalizar la configuración según tus necesidades.



Base de Datos: 
Debes ingresar a phpAdmin y crear una base de datos llamada examen despues inportar el archivo examenisc.sql alojado  en ./Api/Conexion/examenisc.sql , despues debes importar el archivo examenisc.sql, una vez creada debes revisar los usuarios y contraseñas de tu ambiente local y configurar el archivo .env alojado en  ./Api/.env


Información General
Servidor: 127.0.0.1
Versión del Servidor: 10.4.32-MariaDB
Versión de PHP: 8.2.12
Codificación de Caracteres: utf8mb4

Estructura de la Base de Datos

1. Tabla cliente
Descripción: Almacena información sobre los clientes.

Estructura:

sql
Copy code
CREATE TABLE `cliente` (
  `id` int(11) NOT NULL,
  `Nombre` varchar(100) DEFAULT NULL,
  `Apellido_Ma` varchar(100) DEFAULT NULL,
  `Apellido_Pa` varchar(100) DEFAULT NULL,
  `Domicilio` varchar(100) DEFAULT NULL,
  `Correo` varchar(100) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
Datos Iniciales:

sql
Copy code
INSERT INTO `cliente` (`id`, `Nombre`, `Apellido_Ma`, `Apellido_Pa`, `Domicilio`, `Correo`) VALUES
(7, 'skjdaslkd', 'asdq', 'asda', 'asd', 'asdasd@gmail.mx');
Índices:

sql
Copy code
ALTER TABLE `cliente`
  ADD PRIMARY KEY (`id`);
AUTO_INCREMENT:

Estructura:

sql
Copy code
CREATE TABLE `usuario` (
  `id` int(255) NOT NULL,
  `Correo` varchar(255) DEFAULT NULL,
  `Contrasena` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
Datos Iniciales:

sql
Copy code
INSERT INTO `usuario` (`id`, `Correo`, `Contrasena`) VALUES
(3, 'Odin99campos@gmail.com', 'Prueba001'),
(4, 'Isaac@Prueba.com', 'Prueba002');
Índices:

sql
Copy code
ALTER TABLE `usuario`
  ADD PRIMARY KEY (`id`);
AUTO_INCREMENT:

sql
Copy code
ALTER TABLE `usuario`
  MODIFY `id` int(255) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;
Cómo Importar la Base de Datos
Crear la Base de Datos: Antes de importar el SQL dump, asegúrate de haber creado una base de datos llamada examenisc en tu servidor MySQL.

Importar el Dump:

Abre phpMyAdmin.
Selecciona la base de datos examenisc.
Usa la opción de importar para cargar el archivo SQL dump proporcionado.
Verificar la Importación: Asegúrate de que las tablas y los datos se hayan importado correctamente revisando las tablas cliente y usuario en phpMyAdmin.

Notas
Auto Incremento: Los valores de AUTO_INCREMENT son iniciales y pueden ajustarse según las necesidades de tu aplicación.



