**Melakukan Direct ke file `TodoListView` pada method HandleLogin** :

```java
FXMLLoader fxmlLoader = new FXMLLoader(getClass().getResource("/com/example/demo/TodoListView.fxml"));  
Parent todoListPage = fxmlLoader.load();  
Scene currentScene = sayHaiLabel.getScene();  
currentScene.setRoot(todoListPage);
```