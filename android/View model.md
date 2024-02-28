Summary:
1. [[View model#Configuration]] . Awal konfigurasi menerapkan view model
2. [[View model#View Model setup]]. Setup implementasi class  *view model*
3. [[View model#Class `ViewModel`]]. implementasi class *UiState*
4. [[View model#`StateFlow`]]. implementasi `stateFlow` untuk mendeklarasikan *UiState* dengan *View model*
5. [[View model#Variabel dan fungsi]]. penggunaan variabel dan fungsi pada *View model*
6. [[View model#Fungsi dan variabel penghubung]]. penggunaan variabel dan fungsi yang menghubungkan antara *View* dan *View model*
7. [[View model#Meneruskan data *antara `ViewModel` dan `View`*]]. cara menghubungkan data antara *View* dan *View model*
8. [[View model#Akses data pada `UiState`]]. mengkases data pada *UiState* di *View*
9. [[View model#Update `UiState`]]. melakukan update pada *UiState*

## Configuration
``build.gradle.kts (Module :app)

```kotlin

dependencies {
// other dependencies   
implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.6.1")
//...
}

```
*Menambahkan library external pada dependensi*

## View Model setup

### Class `ViewModel`
Membuat class `View Model` sebuah `View`
```kotlin
import androidx.lifecycle.ViewModel

 class GameViewModel : ViewModel() {
 // properties, function, etc
 }
```
*Class `GameViewModel` untuk **View** `GameView` *

View model yang akan bertanggung jawab pada perubahan, pemyimpanan, pengelolahan event/data, dll

### Data class `UiSate`
Membuat class `UiState` dapat dilakukan difle yang berbeda dengan class `View Model`
```kotlin
data class GameUiState(

val currentScrambledWord: String = ""

	)
```
*Class UiState akan sebagai acuan menyimpan data yang akan berubah *

Pada UiState terdapat variabel yang akan menyimpan nilai dan dikomsumsi di-`View`

### `StateFlow`
[Penjelasan tentang StateFlow](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-state-flow/)

```kotlin
import kotlinx.coroutines.flow.MutableStateFlow
```
*Import*

deklarasi variabel didalam sebuah class `ViewModel` yang akan menggunakan `Uistate`
```kotlin
private val _uiState = MutableStateFlow(GameUiState())
```
*deklarasi variabel `UIstate` dengan menggunakan `StateFlow`, `GameViewModel` memanggil `GameUiState`*

agar dapat diakses diluar class alias pada class `View` maka tambahkan properti pendukung ke `_uiState_`
```kotlin
import kotlinx.coroutines.flow.StateFlow// Game UI state
// Backing property to avoid state updates from other classes
private val _uiState = MutableStateFlow(GameUiState())
val uiState: StateFlow<GameUiState> = _uiState.asStateFlow()
```
*kelak pada `View` variabel object `uiState`lah yang akan diakses untuk mendapatkan nilai-nilai dari variabel state*


## Variabel dan fungsi 

Ketika sebuah variabel dalam sebuah `View model` digunakan maka harus menggunakan sebuah fungi publik /`public fun` sebagai `getter`.

### Fungsi dan variabel penghubung
fungsi/variabel yang berhubungan secara langsung dengan fungi/class `View` maka dia memiliki * Public Access modifier* 
```kotlin
// example for a function will accesed in view layer
fun resetGame() {
usedWords.clear()
_uiState.value = GameUiState(currentScrambledWord = pickRandomWordAndShuffle())

}
```
*Fungsi `resetGame` akan dipanggil pada sebuah `event` di`View` *

### Fungsi dan variabel pendukung

apabila sebuah fungsi atau variabel pendukung hanya berkaitan dengan data pada `ViewModel` saja maka akses modifer berstatus `Private`

```kotlin
private lateinit var currentWord: String

private fun pickRandomWordAndShuffle(): String {   // Continue picking up a new random word until you get one that hasn't been used before  
currentWord = allWords.random()   

if (usedWords.contains(currentWord)) { 

return pickRandomWordAndShuffle() 
} else {
usedWords.add(currentWord)
return shuffleCurrentWord(currentWord)   }
}

```
*contoh sederhanan sebuah fungsi yang hanya berkaitan dengan variabel/data pada `ViewModel` saja*


## Meneruskan data *antara `ViewModel` dan `View`*
[Ilustrasi](https://developer.android.com/static/codelabs/basic-android-kotlin-compose-viewmodel-and-state/img/de93b81a92416c23_1920.png?hl=id)
*Pendekatan ini memastikan bahwa setiap kali ada perubahan dalam nilai `uiState`, rekomposisi terjadi untuk composable menggunakan nilai `gameUiState`.*

### Deklarasi `ViewModel`
deklrasi `View Model` pada `Parent component` agar dapat digunakan pada seluruh `Child component`.
```kotlin
@Composable
fun GameScreen(   
gameViewModel: GameViewModel = viewModel()
 ) {
    // ...
    }
```
*Deklrasi `View model` pada parameter `parent component`*

### Deklarasi `UiState`
```kotlin
@Composable
fun GameScreen(   
gameViewModel: GameViewModel = viewModel()
 ) {
	val gameUiState by gameViewModel.uiState.collectAsState()
    }
```

## Penggunaan `ViewModel` dan `UiState`
[[View model#Deklarasi `UiState`]]. pada contoh tersebut terdapat 2 variabel dengan peruntukan yang berbeda, namun variabel *UiState* `gameUiState` diakses melalui turunan *View Model* `gameViewModel`.
Jika ingin mengambil nilai dari properti `UiState` maka,akses dari variabel turunan dari *UiState*`gameUiState` dan jika menggunakan atau memanggil fungsi dari *View model* maka akses melalui variabel turunan dari *View model*`gameViewModel`.

### Akses data pada `UiState`
```kotlin
@Composable
(){
val gameUiState by gameViewModel.uiState.collectAsState()

// memanggil fungsi
GameLayout(   
currentScrambledWord = gameUiState.currentScrambledWord,   
modifier = Modifier )

}


@Composable
fun GameLayout(   
currentScrambledWord: String,   
modifier: Modifier = Modifier) {
// Inside component
}




```

### Akses fungsi dan variabel pada `ViewModel`

jika pada *View Model* terdapat fungsi  `updateUserGuess` dengan argument string, seperti berikut :
```kotlin
// GameViewModel.kt

var userGuess by mutableStateOf("")   
private set;

fun updateUserGuess(guessedWord: String){     
 userGuess = guessedWord  }
```

[[View model#Deklarasi `UiState`]], pada contoh tersebut telah terdeklarasikan variabel Object dari *View Model*, agar dapat mengkases fungsi didalam *View Model* maka kita harus melalui variabel object tersebut `gameViewModel`.

```kotlin
// GameScreen.kt

@Composable
fun GameLayout(   
onUserGuessChanged: (String) -> Unit,   
currentScrambledWord: String,   
modifier: Modifier = Modifier,   ) {
// Inside component
}


GameLayout(   
onUserGuessChanged = { gameViewModel.updateUserGuess(it) },   
currentScrambledWord = gameUiState.currentScrambledWord,
)

```

## Update `UiState`

```kotlin
data class GameUiState(
val currentScrambledWord: String = "",   
val isGuessedWordWrong: Boolean = false,
)
```

```kotlin

import kotlinx.coroutines.flow.update   
if (userGuess.equals(currentWord, ignoreCase = true)) {  
} else {       
// User's guess is wrong, show an error       
_uiState.update { currentState -> currentState.copy(isGuessedWordWrong = true) 
	}   
}
```

**Catatan pada metode copy():** Gunakan fungsi `copy()` untuk menyalin objek, sehingga Anda dapat mengubah beberapa propertinya dan tidak mengubah sisanya.

Contoh:
`val jack =` `User(name =` `"Jack", age =` `1)`
`val olderJack = jack.copy(age =` `2)`




