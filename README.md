# PRACTICA REDUX 

para esta sección construiremos dos mini proyectos que serviran para entender mejor redux.

## Repaso
Redux es un patron de diseño para el mensajo del estado de la aplicación, evitando un flujo de arbol como lo hacemos con los states de react, y teniendo como unidad de estado un store global para todos los componentes.

![](https://github.com/daandradec/redux_ingsoft_II/blob/master/ideas_principales.png)

![](https://github.com/daandradec/redux_ingsoft_II/blob/master/terminologia.png)

## Basicos de Redux

Para esta primera parte crearemos un codigo sencillo usando redux bajo un proyecto de Node


1. Crear una carpeta llamada basicos_redux_node
2. Pararse en esta carpeta
3. Ejecutar node init
4. Por facilidad solo insertar campos como : 
5. una vez creado ejecutar npm install redux
6. Crear en la raiz de basicos_redux_node el archivo basicos_redux.js
7. Copiar el siguiente codigo


```
// REDUX BASICOS

// comando para ejecutarlo parados en el raiz de la carpeta de este archivo: node basicos_redux.js


const redux = require('redux');

const createStore = redux.createStore;

// state inicial
const stateInicial = {
    usuarios: []
}

// Reducer
// state y accion
const reducerPrincipal = (state = stateInicial, action) => {
    if(action.type === 'AGREGAR_USUARIO'){
        return {
            ...state, // copia del state original (contenido que tiene dentro)
            usuarios : action.nombre // modifica unicamente esta llave
        }
    }else if(action.type === 'MOSTRAR_USUARIOS'){
        return {
            ...state
        }
    }

    return state; // returna como nuevo state, el state original
}

// create store, y store (contiene el state de la aplicación)
// 3 parametros, reducer, state inicial, applymiddleware
const store = createStore(reducerPrincipal);

// Suscribe o suscripción
// Se llama cuando el store, para alguna acción utiliza el dispatch o cuando
// el state cambia
store.subscribe(() => {
    console.log('Algo cambio...', store.getState());
})

// Dispatch: es la forma de cambiar el state (ejecuta una acción que modificara el state)
//console.log(store.getState());
store.dispatch({type:'AGREGAR_USUARIO', nombre: 'Juan'} /* Este json es un action formado por un type y un payload*/);
//console.log(store.getState());
store.dispatch({type:'MOSTRAR_USUARIOS'} /* Este json es un action formado por un type y un payload */);
//console.log(store.getState());
```

## REACT Redux

