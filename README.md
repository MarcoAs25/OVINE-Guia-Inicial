# OVINE-Guia-Inicial

## Olá, bem vindo ao guia inicial da engine de criação de Objetos virtuais de aprendizagem Ovine

Sumário

- Introdução
- Como importar e exportar projetos
- Adicionando novos objetos em cenas
  - Hierarquia
  - Outras Ações em Cena
- Parametros e propriedades
- Criando projeto a partir de um projeto base
- Para devs
  - Criando comportamentos 1 - MRU
  - Criando comportamentos 2 - MRUV
  - Aprendendo com erros

# Introdução
[IMAGEM OVINE]
Ovine é uma engine de criação e reprodução de Objetos virtuais de aprendizagem, sua ideia principal é facilitar a criação de OVA por professores leigos em programação. <br>
A engine utiliza o motor de jogos unity como sua plataforma e foi criada com plugins e pacotes multiplataforma, facilitando a portabilidade futura para android e web. <br> 
O intuito da ferramenta é criar uma ponte entre programadores e professores que desejam criar seus OVA para uso dentro de sala de aula. <br>
Atualmente esta ponte é feita por aquivos de script C# que são compilados em tempo de execução através do compilador Roslyn C#, mas futuramente se almeja uma plataforma com visual script integrada a ferramenta, facilitando assim o uso por professores que queiram se aventurar no mundo da criação de scripts para OVA.

# Como Importar e Exportar projetos
A importação e exportação de projetos ocorre através de arquivos compactados em formato .zip, abaixo é disponibilizado um exemplo de arquivo de projeto para a realização das tarefas do presente tutorial, podendo ser feito o download aqui(aqui vai o link).
para a importação de projeto, abra o OVINE e selecione criar, logo em seguida, no canto inferior esquerdo você terá o botão "importar projeto", clique no botão e selecione o aquivo zip baixado.<br>
Logo em seguida, a interface do usuario deverá mudar, e você poderá começar a utilizar o projeto.
Para a exportação de projetos, na sua tela inicial, você pode selecionar o botão criar e logo em seguida selecionar o ícone de exportar, que estará ao lado direito do titulo do seu projetocom isso, selecione o local final do arquivo exportado e pronto! agora é só compartilhar com seus alunos!

# Adicionando novos objetos em cenas
Ovine possui quatro paineis principais, todos eles estão disponíveis caso tenha selecionado a opção de criar ao no menu inicial da engine, sendo eles:
  * Componentes: Utilizado para adicionar novos objetos em cena
  * Hierarquia: Utilizado para visualizar objetos instanciados em cena
  * Propriedades: Utilizado para adicionar comportamentos, imagens, e também modificar posição, rotação e escala do objeto selecionado.
  * Parâmetros: Utilizado para a modificação de variáveis globais ou locais dos objetos (Obs: Estas variáveis são serializáveis, ou seja, o professor pode personalizálas antes de enviar para o aluno).

Para a adição de um novo Objeto de cena, vamos utilizar a aba componentes, ela se encontra no canto esquerdo da cena, e ao abrir você irá se deparar com um dropdown, nele você pode selecionar qual pacote de componentes deseja selecionar o objeto, logo em seguidam será mostrado abaixo do dropdown um grid com todos os objetos que você pode criar na cena.<br>

No canto inferior direito da sua cena, você poderá visualizar 3 bot~eos principais, sendo eles:
  * Salvar: Salva a cena do projeto
  * Executar: Salva e logo em seguida executa a cena do projeto
  * Recarregar: discarta todas as alterações não salvas e recarrega a cena

## Hierarquia
Muitas das vezes pode ser necessário ocultar, renomear ou excluir algum objeto em virtude de edição de cena, estas ações podem ser feitas através da aba de hierarquia, localizada no canto inferior esquerdo da tela.
Conforme mostrado na imagem acima, a aba hierarquia possui, respectivamente as ações:
  - Editar nome: botão amarelo
  - Ocultar/Mostrar: botão azul
  - Excluir objeto: botão vermelho

## Outras Ações em Cena
Você pode notar que na parte superior você possui também uma seção que indica as cenas carregadas daquele projeto, ao selecionar uma delas você salva a cena atual e logo em seguida carrega a cena selecionada, você também possui a ao lado direito do menu, um botão para a adição de novas cenas, podendo ser utilizado para a criação de novas cenas.

# Parametros e propriedades
No canto direito da cena de edição, as abas propriedades e parâmetros são os principais locais para a modificação do programa, através dela é possível fazer as edições dos objetos instanciados e também a edição das variáveis globais e locais do projeto.
Na aba de propriedades, após selecionar um objeto utilizando control + click no objeto, ou selecionar pela aba hierarquia, é possível a modificação da posição do objeto, rotação em x,y e z, e também a rotação do objeto, conforme mostrado na imagem abaixo.

Na aba de propriedades, também é possível adcionar novas imagens ao objeto, estas imagens devem estar dentro da pasta imagens do próprio projeto, mas caso deseja adicionar uma imagem fora deste caminho, a engine irá criar uma cópia para sua pasta automaticamente.
Também é possível adicionar comportamentos aos seus objetos, para isso, ao selecionar o objeto que deseja adicionar um comportamento, será mostrado uma lista de vários comportamentos que podem ser adicionado aos objetos, conforme mostrado na imagem abaixo.

Comportamentos adicionados aos objetos podem adicionar variáveis nos parâmetros para que o usuário possa modificar antes ou durante a execução do programa, conforma é mostrado na imagem abaixo, existem diversas formas de parâmetros que podem ser modificados.
# Criando projeto a partir de um projeto base
No momento da criação de um novo projeto, você geralmente vai preferir a utilização de um projeto como base, já que trás consigo comportamentos, pacotes e exemplos para modificação, para isso, na cena inicial vc pode selecionar a opção criar e no centro superior da tela digitar o nome do seu projeto, logo em seguida abaixo é possível selecionar o projeto que irá ser utilizado como base, e por fim clicar no botão criar.

# Para devs
Para os desenvolvedores ou professores que desejam criar seus próprios comportamentos, é possível realizar a criação dos mesmos através de arquivos .cs, e logo em seguida adicioná-los à pasta behaviours do projeto, abaixo é mostrado um modelo de um arquivo .cs que deve ser utilizado para a criação de novos comportamentos.
```cs
using OvaExamples;
using UnityEngine;
using OvaParameters;
public class NameClass: OvaBehaviour
{
    protected override void Playing()
    {
        base.Playing();
    }
    protected override void Editing()
    {
        base.Editing();
    }
    protected override void Setup()
    {
        base.Setup();
    }
}

```

A função Playing é chamada a cada frame quando o projeto está em execução, já a função Editing é chamada a cada frame quando o projeto está em modo de edição, por fim, a função Setup é chama apenas quando o objeto é instanciado em cena, todas as classes devem herdar de OvaBehaviour para que possuam estas chamadas.

## Criando comportamentos 1 - MRU
Esta seçãos erve como tutorial para a criação de um comportamento de carrinho que anda com a velocidade constante (MRU), além disso, para verificar o tempo gasto do carrinho que percorreu uma distância x.
### Criação do comportamento de carrinho
Para que o carrinho possua movimento, é necessário a adição de um corpo rígido no objeto, para isso, definimos a variável rb2d: 
```cs
public Rigidbody2D rb2d;
```
Para que o programador consiga acessar suas variváveis utiliza-se de um id, a abordagem recomendada é a utilização de um uuid, para que não ocorra possibilidades de conflito com outros comportamentos de terceiros
```cs
private string velocityId = "a21bcf8d-6adb-4352-81bb-434f6a262428";
```
Sempre que for utilizado uma nova variavel para o usuário, utiliza-se o OvaParameterManager, através dele é possível a criação de novas variáveis e também a recuperação dos mesmos.
```cs
  //adiciona um parametro local do tipo inteiro, com um range de 0 a 10, e com valor inicial de 0
  OvaParameterManager.Instance.SetLocalParameter(new Parameter(velocityId, "velocidade em m/s", 0, 10, 0), gameObject);
```

Pode ser que o objeto no qual o componente corpo rígido será adicionado já possua o mesmo, para isso, antes da adição de um novo corpo rígido, é feito uma verificação antes da adição de um novo corpo rígido
```cs
        //tenta pegar o corpo rigido do objeto no qual este comportamento está anexado
        rb2d = GetComponent<Rigidbody2D>();
        //caso não tenha encontrado nenhum corpo rígido, adiciona um novo ao objeto e atribua a variável rb2d
        if (rb2d == null)
        {
            rb2d = this.gameObject.AddComponent<Rigidbody2D>();
        }
```
Depois de inicializar nossas variáveis é possível criar modificações no nosso objeto de acordo com as mesmas, abaixo é mostrado um exemplo de vários parâmetros que podem ser modificados em um corpo rígido
```cs
        //bodyType serve principalmente para definir se o corpo rígido é dinâmico (sofre gravidade, colisão, adição de forças e etc) ou estático (é fixo)
        rb2d.bodyType = RigidbodyType2D.Dynamic;
        //gravityScale define a gravidade que o objeto sofrerá
        rb2d.gravityScale = 0f;
        //mass define a massa do objeto
        rb2d.mass = 10000f;
        //drag e angularDrag define o arrasto
        rb2d.drag = 0f;
        rb2d.angularDrag = 0f;
        //freezeRotation define se haverá rotação no eixo z (se true, o objeto não possuirá rotação)
        rb2d.freezeRotation = true;
        //velocity define a velocidade do objeto
        rb2d.velocity = new Vector2(OvaParameterManager.Instance.GetLocalParameter(velocityId, gameObject).intValue, 0f);
```
O arquivo final é mostrado abaixo, códigos de inicialização ficarão em Setup, e códigos que devem executar durante a execução do programa ficam na função Playing
```cs
using OvaExamples;
using UnityEngine;
using OvaParameters;
public class CarMRUV: OvaBehaviour
{
    public Rigidbody2D rb2d;
    private string velocityId = "a21bcf8d-6adb-4352-81bb-434f6a262428";
    protected override void Playing()
    {
        base.Playing();
        rb2d.bodyType = RigidbodyType2D.Dynamic;
        rb2d.gravityScale = 0f;
        rb2d.mass = 10000f;
        rb2d.drag = 0f;
        rb2d.angularDrag = 0f;
        rb2d.freezeRotation = true;
        rb2d.velocity = new Vector2(OvaParameterManager.Instance.GetLocalParameter(velocityId, gameObject).intValue, 0f);
    }
    protected override void Editing()
    {
        base.Editing();
    }
    protected override void Setup()
    {
        base.Setup();
        OvaParameterManager.Instance.SetLocalParameter(new Parameter(velocityId, "velocidade em m/s", 0, 10, 0), gameObject);
        rb2d = GetComponent<Rigidbody2D>();

        if (rb2d == null)
        {
            rb2d = this.gameObject.AddComponent<Rigidbody2D>();
        }
    }
}
```
## Criando comportamentos 2 - MRUV
Para a criação de um corportamento em MRUV, podemos utilizar o sistema de corpo rígido para a adição de gravidade, para isso, o sistema segue algo bastante similar ao exemplo acima, sendo a principal diferença a inicializão de duas novas variáveis (posição em x e y do botão).
```cs
    protected override void Setup()
    {
        base.Setup();
        //Camera.main.pixelWidth e Camera.main.pixelHeight pega o tamanho da tela em pixels, ex: 1280 x 720, estes serão os valores máximos das variáveis
        OvaParameterManager.Instance.SetLocalParameter(new Parameter(posxId, "posição em x do botao", 0, Camera.main.pixelWidth, 0), gameObject);
        OvaParameterManager.Instance.SetLocalParameter(new Parameter(posyId, "posição em y do botao", 0, Camera.main.pixelHeight, 0), gameObject);
        OvaParameterManager.Instance.SetLocalParameter(new Parameter(forceId, "forca", 0f, 10f, 1f), gameObject);
        rb2d = GetComponent<Rigidbody2D>();

        if (rb2d == null)
        {
            rb2d = this.gameObject.AddComponent<Rigidbody2D>();
        }
    }
```
Neste exemplo, não utilizamos nenhum parâmetro dentro de Playing, mas sim de um novo callback, chamado de OnGUI.
OnGUI é chamado a cada frame e dentro desta função é possível a criação de interfaces do usuário, neste exemplo em específico, vamos adicionar um botão para que o usuário possa adicionar uma força horizontal no objeto, fazemos isso através do código abaixo:

```cs
    void OnGUI()
    {
        //Obtém a posição em x e em y do objeto
        int posx = OvaParameterManager.Instance.GetLocalParameter(posxId, gameObject).intValue;
        int posy = OvaParameterManager.Instance.GetLocalParameter(posyId, gameObject).intValue;

        //Desenha duas caixas para o acompanhamento da velocidade em x e em y
        GUI.Box(new Rect(posx,posy - 40,200,20), "Velocidade em x: " + rb2d.velocity.x);
        GUI.Box(new Rect(posx,posy - 40 - 30,200,20), "Velocidade em y: " + rb2d.velocity.y);
        //Desenha o botão de Aplicar força, caso ele seja pressionado, será adicionado uma força em y instantânea (ForceMode2D.Impulse) ao objeto.
        if(GUI.Button(new Rect(posx, posy, 200, 30), "Aplicar força"))
        {
            rb2d.AddForce(new Vector2(0f, OvaParameterManager.Instance.GetLocalParameter(forceId, gameObject).floatValue), ForceMode2D.Impulse);
        }
    }
```
O arquivo final é mostrado abaixo, conforme é mostrado, não foi necessário a utilização a função Playing, mas sim uma nova função nativa da própria unity, existem diversas funções que podem ser utilizadas em conjunto com scripts com comportamento OvaBehaviour, o recomendado é que você consulte a api da unity.

```cs
using OvaExamples;
using UnityEngine;
using OvaParameters;
public class ApplyForce: OvaBehaviour{
    
    private string forceId = "f447bf5c-1b76-43af-808f-eb742278fbe0";
    private string posxId = "b569f927-7911-42eb-a83c-b18858edf175";
    private string posyId = "bc8ce227-96a1-43e0-b7b2-61d7029b81f1";

    private Rigidbody2D rb2d;
    void OnGUI()
    {
        int posx = OvaParameterManager.Instance.GetLocalParameter(posxId, gameObject).intValue;
        int posy = OvaParameterManager.Instance.GetLocalParameter(posyId, gameObject).intValue;
        GUI.Box(new Rect(posx,posy - 40,200,20), "Velocidade em x: " + rb2d.velocity.x);
        GUI.Box(new Rect(posx,posy - 40 - 30,200,20), "Velocidade em y: " + rb2d.velocity.y);
        if(GUI.Button(new Rect(posx, posy, 200, 30), "Aplicar força"))
        {
            rb2d.AddForce(new Vector2(0f, OvaParameterManager.Instance.GetLocalParameter(forceId, gameObject).floatValue), ForceMode2D.Impulse);
        }
    }

    protected override void Playing()
    {
        base.Playing();
    }
    protected override void Editing()
    {
        base.Editing();
    }
    protected override void Setup()
    {
        base.Setup();

        OvaParameterManager.Instance.SetLocalParameter(new Parameter(posxId, "posição em x do botao", 0, Camera.main.pixelWidth, 0), gameObject);
        OvaParameterManager.Instance.SetLocalParameter(new Parameter(posyId, "posição em y do botao", 0, Camera.main.pixelHeight, 0), gameObject);
        OvaParameterManager.Instance.SetLocalParameter(new Parameter(forceId, "forca", 0f, 10f, 1f), gameObject);
        rb2d = GetComponent<Rigidbody2D>();

        if (rb2d == null)
        {
            rb2d = this.gameObject.AddComponent<Rigidbody2D>();
        }
    }
}
```

## Aprendendo com erros
Sempre que houver um erro ao compilar seu Script, Ovine informa alguns dados que podem te ajudar a corrigir o erro, no exemplo abaixo, é mostrado um código no qual possui a varivável rb2d, porém em nenhum momento atribuo um corpo rígido a mesma, mas mesmo assim tento modificar a variável velocity.

```cs
using OvaExamples;
using UnityEngine;
using OvaParameters;
public class ComportamentoComErro: OvaBehaviour{
    
    private Rigidbody2D rb2d;

    protected override void Playing()
    {
        base.Playing();
    }
    protected override void Editing()
    {
        base.Editing();
        rb2d.velocity = 10f;
    }
    protected override void Setup()
    {
        base.Setup();
    }
}
```
