# Ecommerce - Admin

Este es una plataforma de ecommerce, esta parte es el admin de la misma, en el cual se pueden agregar los productos, categorías, etc. Así como también se manejan las órdenes, se verifican los pagos y se ve el balance de ventas.

## Requisitos previos

Antes de comenzar, asegúrate de tener instalado lo siguiente:

- Node.js y npm (o yarn)
- Git

## Configuración inicial

1. Clona este repositorio en tu máquina local:

    ```bash
    git clone https://github.com/juanosorio0219/ecommerce-admin.git
    ```

2. Instala las dependencias del proyecto:

    ```bash
    npm install
    ```

    O, si usas yarn:

    ```bash
    yarn install
    ```

## Configuración de clerk (Servicio de autenticación)

1. Iniciar sesión en https://clerk.com/

2. Agregar al .env del proyecto lo siguiente:
   ```plaintext
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
   CLERK_SECRET_KEY=
   NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
   NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
   NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/
   NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/
   ```

## Creación de la base de datos

1. Instalación de MySQL  

- En Windows:
Acceder al sitio web oficial de MySQL y descargar el instalador.

- En macOS (con Homebrew):
```bash
brew install mysql
```

2. Iniciar el servidor MySQL
El servidor MySQL debería iniciar automáticamente después de la instalación. Si no lo hace, puedes iniciarlo manualmente con el siguiente comando:

```bash
sudo systemctl start mysql  # Para Linux
brew services start mysql  # Para macOS
```
3. Acceder a MySQL y crear un usuario
```bash
mysql -u root -p
```
Ingresar la contraseña de root cuando se solicite. Una vez que hayas iniciado sesión en MySQL, puedes crear un nuevo usuario y concederle privilegios.

4. Crear un usuario MySQL
```sql
CREATE USER 'nombre_de_usuario'@'localhost' IDENTIFIED BY 'tu_contraseña';
```
Reemplaza 'nombre_de_usuario' y 'tu_contraseña' con el nombre de usuario y la contraseña que deseas utilizar.

5. Conceder privilegios al usuario
```sql
GRANT ALL PRIVILEGES ON *.* TO 'nombre_de_usuario'@'localhost' WITH GRANT OPTION;
```
Este comando otorga todos los permisos al usuario para todas las bases de datos y tablas. Si deseas restringir los permisos a bases de datos específicas, puedes ajustar la consulta en consecuencia.

6. Actualizar los privilegios
```sql
FLUSH PRIVILEGES;
```

7. Salir de MySQL
```sql
EXIT;
```

8. Conexión a MySQL con el nuevo usuario
```bash
mysql -u nombre_de_usuario -p
```
Ingresa la contraseña del usuario cuando se te solicite.

9. Crear una nueva base de datos
Una vez que hayas iniciado sesión con el nuevo usuario, puedes crear una nueva base de datos.

```sql
CREATE DATABASE nombre_de_base_de_datos;
```

10. Verificar que la base de datos se creó correctamente
```sql
SHOW DATABASES;
```

11. Salir de MySQL
```sql
EXIT;
```

12. Agregar la bd al .env del proyecto
    
```plaintext
DATABASE_URL="mysql://usuario:contraseña@localhost:3306/nombre_de_base_de_datos"
```

## Conectar la bd, y usar Prisma para inicializar las tablas

```plaintext
npx prisma generate or npx prisma generate ./prisma/schema.prisma 
npx prisma db push
```



   


