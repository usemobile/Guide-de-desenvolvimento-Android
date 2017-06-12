# Guia de estilo Android
 
Esse guia de estilo é um produto da nossa equipe de desenvolvimento Android. Reflete regras de programação da linguagem Java que observamos ser eficientes no desenvolvimento de nossos projetos de aplicativos.
 
As diretrizes que aqui serão apresentadas encorajam práticas que buscam atingir as seguintes metas:
 
* Fazer com que seja mais difícil escrever erros de programação, ou então facilitar a busca e correção de erros.
* Melhorar a organização tanto para facilitar a leitura quanto melhorar a clareza do conteúdo. Tendo em vista que um mesmo projeto pode ser desenvolvido por mais de uma pessoa e também pode ser revisado por outra pessoa.
 
Alguns dos padrões que aqui podem ser observados podem opor os padrões seguidos pela comunidade Android, porém ressaltamos que testamos e utilizamos essas práticas em nossa equipe e as mesmas se mostraram mais eficientes até o presente momento.
 
Esse guia de estilo foi feito com base no que encontramos de mais relevante em guias de estilo utilizados no mercado em conjunto com a experiência da nossa equipe.
 
Dito isso, esse é um documento que será atualizado constantemente, à medida que nossa equipe e a linguagem Java evoluam, nossas práticas irão se adaptar acompanhando essas mudanças. Esse guia foi atualizado pela última vez em _ de _ de 2017.
 
 
## 1. Formatação de código
 
* **1.1.** Use 4 espaços para tabs. Configure-os da seguinte forma:
 
![whatsapp image 2017-06-12 at 16 30 02](https://user-images.githubusercontent.com/22510341/27051474-a672ea46-4f8c-11e7-94a8-d65678aa3cb5.jpeg)
 
* **1.2.** Utilizar o comando de indentação do Android Studio, e não alterar nada depois. O comando pode ser feito com o atalho ***Ctrl+ alt + l*** no Windows, ***Ctrl + shift + alt + l*** no Linux e ***option + command + l*** no Mac.
 
* **1.3.** A abertura de chaves deve seguir na mesma linha da Classe, método, função e etc.
```java
//Certo
class UseClass{
    private void useMethod(){
        if(x == y){
            //código
        }
    }
}
 
//Errado
class UseClass
{
    private void useMethod()
    {
        if (x == y)
        {
            //código
        }
    }
}   
```
 
* **1.4.** Todas as funções devem ser separadas uma da outra por uma linha vazia.
```java
// Certo
class UseClass{
    // ...
    
    private void useMethod(){
        // ...
    }
 
    private void useMethod2(){
        // ...
    }
}
 
//Errado
class UseClass{
    // ...
    
    private void useMethod(){
        // ...
    }
    private void useMethod2(){
        // ...
    }
}
```
 
* **1.5.** Ao usar vírgula (' , ') deve ser adicionado um espaço depois e não conter espaço algum antes.
 
```java
//Certo
void useFunction(int p1, int p2, int p3){
    /** **/
}
 
//Errado
void useFunction(int p1,int p2,int p3){
    /** **/
}
```
 
* **1.6.** Inserir um espaço antes e depois de operadores binários ('+ , -, /, e etc') e conter um espaço antes de abrir parênteses e um depois de fechar.
```java
//Certo
int useConstant = 5 + (10 / 2) * 6 - 10;
 
if (1 + 1 == 3) {
    //Código
}
 
//Errado
int useConstant = 5+(10/2)*6-10;
 
if(1+1==3) {
    //Código
}
```
 
* **1.7** Nunca use mais de uma linha em branco consecutiva. Use uma linha de separação em branco para separar áreas dos códigos com contextos diferentes. NUNCA use uma nova linha em branco depois de abrir uma chave.
```java
//Certo
public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
 
        // set up foo object
        Foo foo = new Foo();
        foo.setProperty(value);
 
        // set up bar object
        Bar bar = new Bar(foo);
    }
 
 //Errado
 public void onCreate(Bundle savedInstanceState) {
 
        super.onCreate(savedInstanceState);
        // set up foo object
        Foo foo = new Foo();
        foo.setProperty(value);
        // set up bar object
        Bar bar = new Bar(foo);}
```
 
* **1.8.** Quando chamar função de múltiplos parâmetros, colocar cada parâmetro em um linha.
```java
//Certo
void useFunction(int p1,
                  int p2,
                  int p3);
                 
 
//Errado
void useFunction(int p1, int p2, int p3);
```
 
* **1.9.** Para linhas grandes sempre quebre-as antes de uma chamada de método, depois de vírgulas ou depois de um operador.
```java
//Certo
AlertDialog.Builder builder = new AlertDialog.Builder(context)
                              .setTitle("MyTitle")
                              .setMessage("MyMessage")
                              .setView(customView);          
                 
//Errado
AlertDialog.Builder builder = new AlertDialog.Builder(context).setTitle("MyTitle").setMessage("MyMessage").setView(customView);
```
 
* **1.10.** Usar constantes locais ou outras técnicas de mitigação para evitar múltiplas linhas.
```java
//Certo
boolean firstCondition = x == firstReallyReallyLongPredicateFunction();
boolean secondCondition = y == secondReallyReallyLongPredicateFunction();
boolean thirdCondition = z == thirdReallyReallyLongPredicateFunction();
if (firstCondition && secondCondition && thirdCondition){
    //do something
}
 
//Errado
if (x == firstReallyReallyLongPredicateFunction()
    && y == secondReallyReallyLongPredicateFunction()
    && z == thirdReallyReallyLongPredicateFunction()){
        // do something
}
                 
//Errado
AlertDialog.Builder builder = new AlertDialog.Builder(context).setTitle("MyTitle").setMessage("MyMessage").setView(customView);
```
 
## 2. Organização das classes
* **2.1.** Em geral, a organização é papel do auto-formatador do Android Studio.
* **2.2.** A visibilidade deve seguir a seguinte ordem:
 
        * Static
        * Public
        * Protected
        * Package private
        * Private
* **2.3.** Divida a classe em regiões. Geralmente os arquivos das classes têm as seguintes regiões:
 
        * Constants(publicas, depois privadas) -> Constants
        * Declarações de interface -> Interface Declarations
        * Enums -> Enums
        * Variáveis estáticas com quaisquer métodos associados(públicas, depois privadas) -> Statics
        * Variáveis membras -> Members
        * Construtores -> Constructors
        * Getters e Setters -> Acessors
        * Métodos do ciclo de vida Android -> Lifecyle
        * Inherited / métodos de Interface -> Interface Methods
        * Métodos Abstract -> Abstract Methods
        * Quaisquer outros métodos (publics, protected e private nessa ordem) -> Instance Methods
        * Membros anônimos da classe -> Anonymous Classes
        * Definições de classes inseridas (primeiro as static) -> Inner Classes
        
* **2.4.** Em geral, use regiões para cada uma dessas seções. SEMPRE nomeie com *endRegion* uma região que é começada com *region*.
```java
// region Constants
    //..código
// endregion Constants
```
Exemplo de um arquivo de classe:
```java
public class MyView extends ViewGroup {
 
    // region Constants
 
    public static final String EXTRA_BAR = "Bar";
    private static final String TAG_FOO = "Foo";
 
    //endregion Constants
 
    // region Interfaces
 
    public interface ActionListener {
 
        /*
         * Put a comment here to describe this method
         */
        public void onActionPerformed(Object action);
    }
 
    //endregion Interfaces
 
    // region Statics
 
    public static Object getThing() {
        return null;
    }
 
    // endregion Statics
 
    // region Members
 
    private int textColor;
    
    private LinearLayout itemLayout;
    
    // endregion Members
 
    // region Constructors
 
    public MyView(Context context, AttributeSet attrs, int defStyle) {
        super(context, attrs, defStyle);
    }
 
    // endregion Constructors
 
    // region Accessors
    
    public int getTextColor() {
        return textColor;
    }
    
    public void setTextColor(int color) {
        this.textColor = color;
    }
    
    public int getItemCount() {
        return itemLayout.getChildCount();
    }
    
    // endregion Accessors
 
    // region Lifecycle Methods
 
    @Override
    protected void onAttachedToWindow() {
        super.onAttachedToWindow();
    }
 
    @Override
    protected void onDetachedFromWindow() {
        super.onDetachedFromWindow();
    }
 
    // endregion Lifecycle Methods
 
    // region Inherited Methods
 
    @Override
    public boolean requestFocus(int direction, Rect previouslyFocusedRect) {
        ...
    }
 
    // endregion Inherited Methods
 
    // region Methods
 
    public void sortChildren() {
        ...
    }
 
    // endregion Methods
 
    // region Anonymous Classes
 
    private final OnClickListener childClickListener = new OnClickListener() {
        @Override
        public void onClick(View v) {
            ...
        }
    };
 
    // endregion Anonymous Classes
 
    // region Inner Classes
 
    private static class StateHelper {
        ...
    }
 
    // endregion Inner Classes
}
```
 
## 3. Nomenclatura
 
* **3.1.** Usar camelCase para funções, métodos, variáveis, argumentos.
```java
//Certo
private int numero;
 
public void useFunction();
 
//Errado
private int mNumero;
 
private void UseFunction();
```
 
* **3.2.** Utilizar UpperCamelCase para os nomes das classes. Para as *activities* e *fragments* utilizar o padrão
*nomeActivity* ou *nomeFragment*.
 
* **3.3.** Nomes devem ser sempres descritivos. Se para isso eles tenha que ser longos é extremamente aceitável. No dê a variáveis ou métodos nomes genéricos, a não ser que o propósito seja genérico.
```java
//Certo
public TextView getTitleTextView() {
    return titleTextView;
}
 
//Errado
 public TextView getTextView() {
    return textView;
}
```
 
* **3.4.** Identificadores nos nomes devem ser ordenados do mais geral para o mais específico. Isso mantém os identificadores na mesma ordem da convenção de nomeação dos pacotes e das classes.
```java
//Certo
public static final String TAG_FRAGMENT_PRODUCT_DETAILS = "ProductDetailsFragment";
 
//Errado
public static final String PRODUCT_DETAILS_FRAGMENT_TAG = "ProductDetailsFragment";
```
 
* **3.5.** Para os layouts, utilizar o padrão *nomedaclasse_tipo_funcao* para os *ids* de todas as *views*. Utilizar os seguintes prefixos:
 
        * `activity` - para layouts usados como conteúdos de uma Activity.
        * `fragment` - para layouts usados como conteúdos de uma Fragment.
        * `layout` - para layouts usados no <include /> ou importados de alguma maneira dentro de outra view.
        * `list_item` - para layouts usados como um item ou uma célula dentro de uma list.
        * `view` - para layouts que são usados como uma peça de uma custom view.
        * Caso não seja nenhum dos itens acima, usar algo que descreva o uso de uma maneira similar às mostradas acima.
        
 ```java
    activity_home.xml
    list_item_product.xml
    view_special_button.xml
 ```
 
* **3.4.** Definir os nomes dos drawables da seguinte forma:
 
| Tipo de ativos | Prefixo       | Exemplo       |
| -------------  | ------------- | ------------- |
| Action bar     | `ab_`         | `ab_useActionBar.png` |
| Button         | `btn_`        | `btn_accept_pressed.png` |
| dialog         | `dialog_`     | `dialog_bottom.pnt` |
| Divider        | `divider_`    | `divider_vertical.png` |
| Icon           | `ic_`         | `ic_home.png` |
| Menu           | `menu_`       | `menu_home.png` |
| Notification   | `notification_` | `notification_bg.png` |
| Tabs           | `tab_`        | `tab_pressed.png` |
 
* **3.5.** Para os ativos que possuem estados, adicionar os estados no final do nome da seguinte forma:
 
| Estado         | Sufixo        | Exemplo       |
| -------------  | ------------- | ------------- |
| Normal | `_normal` | `btn_accept_normal.png` |
| Pressed | `_pressed` | `btn_accept_pressed.png`|
| Focused | `_focused` | `btn_accept_focused.png` |
| Disabled | `_disabled` | `btn_accept_disabled.png` |
| Selected | `_selected` | `btn_accept_selected.png` |
 
* **3.6.** Constantes devem sempre ter todas as letras maiúsculas e separadas por _.
```java
//Certo
static final String USE_NAME = "UseMobile";
 
//Errado
static final String use_Name = "UseMobile";
```
 
* **3.7.** A nomeação de alguns elementos devem ser especiais. Seguir o seguinte padrão para os seguintes elementos:
 
| Elemento         | Prefixo        | Exemplo       |
| -------------  | ------------- | ------------- |
| SharedPreferences | `PREF_` | `PREF_EMAIL` |
| Bundle | `BUNDLE_` | `BUNDLE_AGE`|
| Fragments Arguments | `ARGUMENT_` | `ARGUMENT_USER_ID` |
| Intent Extra | `EXTRA_` | `EXTRA_INTENT` |
| Intent Action | `ACTION_` | `ACTION_USER_ACTION` |
 
## 3. Estilo de Código
 
### 3.1. Geral
 
**3.1.1** Evitar criar variáveis globais a não ser que seja estritamente necessário.
 
**3.1.2** Utilizar ao máximo as funções já existentes do Java. Não há necessidade de escrever código de ordenação, por exemplo.
 
**3.1.3** Quebrar as linhas quando o conteúdo for muito grande.
 
**3.1.4**Deixar os overrides na mesma ordem do ciclo de vida da activity/fragment. Por exemplo:
```java
public class MainActivity extends Activity {
 
//Ordem compatível com o ciclo de vida
    @Override
    public void onCreate() {}
 
    @Override
    public void onResume() {}
 
    @Override
    public void onPause() {}
 
    @Override
    public void onDestroy() {}
 
}
```
 
* **3.1.5** ?????? Bibliotecas override fica por último
 
* **3.1.6** Escreva `this.` sempre dentro de uma classe sempre que for acessar ou modificar um parâmetro próprio da classe.
 
### 3.2. Switch/If
 
* **3.2.1** Switch - Não usar o default caso ele não exista. Por exemplo:
```java
 
switch (expression) {
           case 1:
               // case 1 code
           break;
           case 2: // fall-through
           case 3:
               // code executed for values 2 and 3
           break;
           default:
               // default code
           break;
}
```
* **3.2.2** If- Não usar chaves para comandos de apenas uma linha. Por exemplo:
```java
 
//CERTO
 if (expression) {
        // if code
        // if code
} else if (other expression) {
        // else if code
        // else if code
} else {
        // else code
        // else code
}
if (expression) a=b;
 
 
//ERRADO
 if (expression) {
        a=b;
 } 
 
 
```
### 3.3. Comentários
* **3.3.1** Comente qualquer parte do código que pareça estranha ou intimidante para um novo desenvolvedor.
 
* **3.3.2** Use //TODO em todas as partes do código que foram deixadas incompletas intencionalmente.
 
* **3.3.3** Usar comentários em bloco apenas para o javadoc em classes, interfaces, variáveis ou declaração de métodos.
 
* **3.3.4** Utilizar Javadoc em funções mais complexas, e em bibliotecas que serão utilizadas por outras pessoas além de você.
 
### 3.4. Tratamento de exceções
* **3.4.1** Tratar cada exceção de maneira isolada, nunca fazer genérico. Nunca faça isso:
```java
 
try {
    someComplicatedIOFunction();        // pode ter IOException
    someComplicatedParsingFunction();   // pode ter ParsingException
    someComplicatedSecurityFunction();  // pode ter SecurityException
} catch (Exception e) {                 // Pegou todas as  exceptions
    handleError();                      // com um único handler genérico!
}
 
```
 
### 3.5. Imports
* **3.5.1**     - Importar sempre bibliotecas específicas (não usar com *):
``` java
import foo.*; // errado
import foo.Bar; // certo
```
 
### 3.6. Strings e Colors
* **3.6.1** Sempre colocar no arquivo xml correspondente.
 
* **3.6.2** Padrão de prefixos String:
 
| Prefixo         | Descrição       |
| -------------  | ------------- |
| error_ | Mensagem de erro |
| msg_ | Mensagem qualquer |
| title_ | Título de alguma coisa |
| action_| Alguma ação como "Salvar" |
 
### 3.7. Pacotes
 
* **3.7.1** Cada pacote reservado para uma activity. Por exemplo:
 
![print](https://user-images.githubusercontent.com/22510341/27050944-bcd2af94-4f8a-11e7-9b9c-f21925287ecc.png)
 
 
 
### 3.8. Parâmetros
 
* **3.8.1** O Context sempre virá como o primeiro parâmetro e o Callback será o último. Por exemplo:
 
 
```java
//CERTO
 
// Context sempre primeiro
public User loadUser(Context context, int userId);
 
// Callbacks sempre por último
public void loadUserAsync(Context context, int userId, UserCallback callback);
 
//ERRADO
 
public User loadUser(int userId, Context context);
 
public void loadUserAsync(Context context, UserCallback callback, int userId);
 
``` 
  
 
## 5. Git
### 5.1 Trabalhar no branch.
### 5.2 Commit apenas na master.
### 5.3 Comentar o nome da classe que alterou e descrever a alteração.
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
