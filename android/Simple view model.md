
## configuration :
`build.gradle.kts`
```kotlin
dependencies {  
// latest stable version on https://androidx.tech/artifacts/lifecycle/lifecycle-viewmodel-compose
    val lifecycle_version = "2.6.2"  
    implementation("androidx.lifecycle:lifecycle-viewmodel-compose:$lifecycle_version")
    }
```

## Create *View Model* class
```kotlin
class CounterViewModel: ViewModel() {  
  
    var numberData by mutableStateOf(0)  
        private set // for make sure its only can mutate in this View model  
    fun increseNumber(){  
        numberData -= 1;  
    }  
  
    fun decreseNumber(){  
        numberData += 1;  
    }  
}
```

## Create View function

declare *View model* variable
```kotlin
import androidx.lifecycle.viewmodel.compose.viewModel
@Composable  
fun ConterView() {  
  
    val counterViewModel = viewModel<CounterViewModel>()  
    
  
        
}
```

implement variable and function from *View model*
```kotlin
import androidx.lifecycle.viewmodel.compose.viewModel
@Composable  
fun ConterView() {  
  
    val counterViewModel = viewModel<CounterViewModel>()  
  
    Column (  
        horizontalAlignment = Alignment.CenterHorizontally,  
        verticalArrangement = Arrangement.Center  
    ){  
        Text(  
            text = "Simple Counter",  
        )  
        Text(  
            text = counterViewModel.numberData.toString(),  
            fontWeight = FontWeight.Bold  
        )  
        Row (  
            modifier = Modifier  
                .padding(top= 10.dp),  
            horizontalArrangement = Arrangement.spacedBy(10.dp)  
        ){  
            Button(onClick = {  
                counterViewModel.increseNumber()  
            }) {  
                Text(text = "Tambah")  
            }  
            Button(onClick = {  
                counterViewModel.decreseNumber()  
            }) {  
                Text(text = "Kurang" )  
            }  
        }    }}
```