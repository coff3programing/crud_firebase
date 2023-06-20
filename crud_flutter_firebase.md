# C.R.U.D Firebase y Flutter

A continuación te mostraré cómo crear una lista de tareas utilizando Firebase y Flutter paso a paso :smile:

1. Configuración del proyecto:

- Crea un nuevo proyecto en Firebase (https://console.firebase.google.com) y habilita Firestore como base de datos.
- Configura tu proyecto de Flutter para que se conecte a Firebase siguiendo los pasos en la documentación de Firebase (https://firebase.flutter.dev/docs/overview).

2. Configuración de dependencias: Abre el archivo pubspec.yaml de tu proyecto Flutter y asegúrate de tener las siguientes dependencias: Configuración de dependencias:

```Dart
dependencies:
  flutter:
    sdk: flutter
  cloud_firestore: ^3.1.0
```

3. Configuración de acceso a Firestore: Importa el paquete de Firebase en tu archivo de Dart:

```Dart
import 'package:cloud_firestore/cloud_firestore.dart';
```

Obtén una instancia de Firestore en tu archivo de Dart:

```Dart
final FirebaseFirestore firestore = FirebaseFirestore.instance;
```

4. Creación de la interfaz de usuario: Crea una interfaz de usuario básica en Flutter para mostrar la lista de tareas. Puedes utilizar widgets como ListView, ListTile y CheckboxListTile para mostrar y gestionar las tareas.

5. Obtención de tareas desde Firestore: Utiliza el siguiente código para obtener las tareas desde Firestore y mostrarlas en tu interfaz de usuario:

```Dart
Stream<QuerySnapshot<Map<String, dynamic>>> getTasks() {
  return firestore.collection('tasks').snapshots();
}
```

6. Agregar una nueva tarea:

- Crea un formulario en tu interfaz de usuario para permitir a los usuarios agregar nuevas tareas. Puedes utilizar un TextFormField para que los usuarios ingresen el nombre de la tarea.
- Al enviar el formulario, utiliza el siguiente código para agregar la tarea a Firestore:

```Dart
Future<void> addTask(String taskName) {
  return firestore.collection('tasks').add({
    'name': taskName,
    'completed': false,
  });
}
```

7. Actualización de tareas completadas:
   Para marcar una tarea como completada, puedes utilizar el siguiente código en tu interfaz de usuario:

```Dart
Future<void> updateTaskCompletion(String taskId, bool completed) {
  return firestore.collection('tasks').doc(taskId).update({
    'completed': completed,
  });
}
```

8. Eliminación de tareas: Para eliminar una tarea, puedes utilizar el siguiente código en tu interfaz de usuario:

```Dart
Future<void> deleteTask(String taskId) {
  return firestore.collection('tasks').doc(taskId).delete();
}
```

Resultado: Con estos pasos, habrás creado una lista de tareas básica utilizando Firebase y Flutter

![Todo-List](https://esflutter.dev/assets/get-started/ios/step4-infinite-list-70ea9d8fd7191fb3726f1743bb03499815f93df4f42b687cfd7916052c35eb07.png)
