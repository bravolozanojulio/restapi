# Implantación RestAPI


iniciar proyecto node.js

npm init -y   // Se crea el package.json


instalar typescript local si no se instaló global

npm i typescript --save-dev         //Local
npm i typescript -g                //Global


Iniciar proyecto typescript

tsc --init                        // Global. Se crea el tsconfig.json
npx tsc --init                    // Local. Se crea el tsconfig.json

Cambiamos la configuración del tsconfig.json
"target": "es6",
"outDir": "./build",

Instalación de express, mongoose y morgan, estos son los modulos que utilizaremos 


npm i express mongoose morgan


Instalamos los tipos de datos y módulos de desarrollo

npm install @types/node @types/mongoose @types/express @types/morgan nodemon typescript -D


// Configuramos el .gitignore con:
// Atención no ignorar build si lo vamos a subir a heroku 
node_modules
// Creamos la carpeta src con server.ts   //Archivo typescript
Con el contenido que presentamos¨:
import express from 'express'
import morgan from 'morgan'
class Server {
    private app: express.Application
    constructor(){
        this.app = express()
        this.config()
    }
    config(){
        this.app.set('port', process.env.PORT || 3000)
        this.app.use(morgan('dev'))  // Para que muestre las url invocadas
    }
    routes(){

    }
    start(){
        this.app.listen(this.app.get('port'), 
        () => {
            console.log(`Server on port: ${this.app.get('port')}`)
        })
    }
}
const server = new Server()
server.start()




// Cambiamos el package.json con:
  "scripts": {
    "ts": "tsc -w",
    "dev": "nodemon ./build/server.js",
    "start": "node ./build/server.js"
  },

  // Para compilar
  npm run ts  // que como tiene el -w incorporado se compilará si cambiamos el código
  // Para ejecutar en desarrollo
  npm run dev  // que como tiene el nodemon se reiniciará el servidor si cambiamos
                // además como tenemos 
  // Para ejecutar en producción
  npm start
  


// Ya podemos invocar con localhost:3000