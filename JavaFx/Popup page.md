**Melakukan popup file `TodoListView` pada method HandleLogin** :
``` java
void HandleLogin(ActionEvent event) throws IOException {  
FXMLLoader todoListRoot = new FXMLLoader(getClass().getResource("path/TodoListView.fxml"));  
Parent detailPageRoot = todoListRoot.load();  
TodoListController todoListController = todoListRoot.getController();  

Stage stage = new Stage();  
stage.setScene(new Scene(detailPageRoot));  
stage.show();  
}
```

