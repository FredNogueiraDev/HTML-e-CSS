# HTML - Minhas Anotações
### Elementos semânticos

- `blockquote` : bloco de citação
- `cite` : autor da citação
- `header` : cabeçalho (pode mais de um por página)
- `nav` : barra de navegação (geralmente dentro do header)
- `main` : conteudo principal (um por página, dentro do body)
- `article` : artigo (dentro do main)
- `aside` : conteúdos levemente relacionados (glossário, biografia, etc)
- `footer` : rodapé (autor, contato, copyright, sitemap, etc)
- `section` : seção, componente de outra tag, tem título e conteúdo

### Elementos genéricos

- `div` : elemento de bloco, usar classes para mais significado
- `span` : elemento de texto, usar classes para mais significado

## Ver e Ouvir

- `video`

Aceita os atibutos: src, controls, width, height, autoplay, preload="metadata ou none", loop, muted, poster="./thumbnail.png".

```jsx
<video src="./video.mp4" controls>
  <p>alt text</p>
</video>
```

Fallback content:

```jsx
<video controls>
  <source src="./video.mp4" type="video/mp4" />
  <source src="./video.avi" type="video/avi" />
  <p>alt text</p>
</video>
```

- `audio`

Semelhante a tag `video`.

- `iframe` : inline frame element

Adiciona conteúdo externo.

Aceita os atributos: src, width, height, title (para acessibilidade), allow="", allowfullscreen, frameborder="0", style

- `img`

Aceita os atributos: src, width, height, alt, title...

```jsx
<img
  src="https://source.unsplash.com/random"
  alt="alt text"
  title="titulo da imagem"
/>
```

- `figure`

Adiciona imagens de maneira semântica, aceitando captions, por exemplo:

```jsx
<figure>
  <img src="" alt="" />
  <figcaption>Image caption</figcaption>
</figure>
```

- `svg`

Scalable Vector Graphics, imagens vetorizadas. Aceita atributos como width e height e tags filhas para descrever elementos, como `circle`, `rect`...

Se for um arquivo, pode ser adicionado com a tag `img`

## Formulários

- `form`

Atributos básicos:

- *Action*: para onde o formulário vai ser submetido, se vazio envia para a página onde estou
- *Method*: método http para envio (GET, POST...)

```jsx
<input action="login" method="post"></form>
```

Para deixar o formulário mais semântico, utilizar as tags `fieldset` e `legend`:

Atributos:

- *disabled* desativa a entrada de dados.
- *form=""* referencia o ID de um form, caso a tag `fieldset` fora da tag `form`.
- *name=""* define o nome do grupo.

Elemento `label`: serve para associar ou identificar uma ou mais tags de entrada de dados, utilizar o atributo *for=""* para referenciar um ID de uma tag `input`.

Elemento `button`: representa um botão e é utilizado para envia os dados de um formulário.

Atributos:

- *type=""*: pode ser submit, reset ou button
- *autofocus*: foco automático
- *disabled*: desativa o botão
- *name=""*: key para o conteúdo passado por *value*
- *value=""*: valor que será passado
- *form=""*: link com o ID de um form

```jsx
<form action="">
  <fieldset name="inputs-contact">
    <legend>Contato</legend>
    <label for="">Nome</label>
    <input type="text" />
    <button type="submit">Enviar</button>
  </fieldset>
</form>
```

Elemento `datalist`: dropdown com uma lista de valores como sugestão a uma tag `input`, porém os valores são apenas sugestões, não são obrigatórios. O usuário pode digitar no campo. Cada opção da lista é dada por uma tag `option`.

```jsx
<input type="text" list="fruitsdata" placeholder="Escolha uma fruta" />

<datalist id="fruitsdata">
  <option>maça</option>
  <option>banana</option>
  <option>manga</option>
  <option>laranja</option>
</datalist>
```

**Tag `input`:**

Atributos:

- *type=""*: text, date, number, file, email password...
- *name=""*
- *id=""*
- *autocomplete=""*: busca valores de um certo tipo para sugerir autocomplete
- *autofocus*: foco automático do cursor
- *value=""*: valor pré preenchido automaticamente no campo
- *disabled*: bloqueia o campo para edição
- *readonly*: bloqueia o campo para edição
- *form=""*: referencia o ID de uma tag `form`
- *name=""*: key para os valores enviados ao backend
- *required*: campo de preenchimento obrigatório
- *placeholder=""*: texto sugestivo dentro do campo

**Tipo *password* - `<input type="password">`:**

```jsx
<input
  type="password"
  pattern="[0-9a-fA-F]{4, 8}"
  title="Coloque um HEX de no min 4 e max 8 caracteres"
/>
```

Atributos:

- *minlength=""* / *maxlength=""*: limite o número de caracteres.
- *pattern=""*: expressão regular para validar o que está sendo digitado no campo, ex: `pattern="[0-9a-fA-F]{4,8}"` valida se a entrada contém somente letras e números, no mínimo 4 e no máximo 8 caracteres.
- *title*: é exibido junto com o balão de erro quando o formulário não pode ser enviado.
- *placeholder*
- *readonly*
- *disabled*
- *required*
- *inputmode=""*: configura o tipo de teclado que deve aparecer: numeric, por exemplo
- *autocomplete=""*: ligado/desligado: "on/off", tem outras opções

**Tipo *email* - `<input type="email">`:**

Espera que o usuário entre um email e faz uma validação básica.

Atributos:

- *placeholder=""*
- *value=""*: valor previamente preenchido no campo
- *readonly*
- *disabled*
- *required*
- *multiple*: aceita várias entradas separadas por vírgula
- *minlength / maxlength*
- *size=""*: tamanho do campo em número de caracteres
- *pattern*: regex, por ex, apenas emails do domínio aluno: `pattern=".+@aluno\.com\.br"`
- *title*: o title é mostrado quando um valor inválido tenta ser enviado
- *list*: faz link com um ID de uma `datalist` para sugestões

**Tipo *URL* - `<input type="url">`:**

Espera que o usuário digite uma URL e faz validação.

Atributos:

- *placeholder=""*: ex. [http://example.com](http://example.com/)
- *value=""*: valor previamente preenchido no campo
- *readonly*
- *disabled*
- *required*
- *minlength / maxlength*
- *size=""*: tamanho do campo em número de caracteres
- *pattern*: regex
- *list*: faz link com um ID de uma `datalist` para sugestões
- *spellcheck="true"*: habilita correção ortográfica neste campo

**Tipo *file* - `<input type="file">`:**

Permite o usuário escolher um ou mais arquivos para enviar no formulário.

Atributos:

- *value=""*: contém o arquivo a ser enviado
- *accept=""*: descreve os tipos de arquivos aceitos, ex: .doc, .png, image/*
- *files*: lista de arquivo(s) a serem enviados
- *multiple*: permite o envio de múltiplos arquivos

Para enviar arquivos, a tag `form` deve possuir um atributo *action=""*, com o destino, *method="post"*, e *enctype="multipart/form-data"*:

```jsx
<form action="" method="post" enctype="multipart/form-data">
  <input type="file">
  <button>Send</button>
</form>
```

**Tipo *color* - `<input type="color">`:**

Interface para selecionar uma cor

Atributos:

- *value=""*: RGB, se for inválido, será exibido preto
- *list*: faz link com um ID de uma `datalist` para sugestões

**Tipo *checkbox* - `<input type="checkbox">`:**

Caixas de seleção que podem ser marcadas/desmarcadas. Seleciona um valor a ser enviado. Se estiver desmarcado, nao envia nada. Se estiver marcado, envia o nome=on.

Atributos:

- *name*
- *value=""*: valor que é passado, por padrão é "on"
- *checked*: estado inicial marcado

Para várias caixas, utiliza o mesmo *name* e trocar os *value*.

**Tipo *hidden* - `<input type="hidden">`:**

Invisível para o usuário, porém é enviado junto com o formulário. Por exemplo, para enviar um timestamp.

**Tipo *radio* - `<input type="radio">`:**

Permite a seleção de uma única opção em uma lista (com bolinhas).

Atributos:

- *checked*: indica o campo marcado inicialmente
- *value*: valor que o campo contém

**Tipo *search* - `<input type="search">`:**

Usado para campos de busca. Igual ao tipo "text", porem podendos ser diferente dependendo do user agent (navegador).

Atributos:

- *list*: faz link com uma `datalist`
- *pattern*: regex
- *aria-label*: opção de acessibilidade quando não se pode usar `label`

**Tipo *number* - `<input type="number">`:**

Espera uma entrada numérica.

Atributos:

- *min="" / max=""*
- *step*

**Tipo *range* - `<input type="range">`:**

Exibe um controle para selecionar um valor numérico. Pode ser um slider ou dial control.

Atributos:

- *min="" / max=""*
- *step*

**Tipo *date* - `<input type="date">`:**

Exibe um calendário para selecionar uma data.

**Tipo *datetime-local* - `<input type="datetime-local">`:**

Utilizado para selecionar data e hora.

**Tipo *month* - `<input type="month">`:**

Utilizado para selecionar um mês.

**Tipo *week* - `<input type="week">`:**

Utilizado para selecionar uma semana.

**Tipo *time* - `<input type="time">`:**

Utilizado para selecionar uma hora.

**Tag `textarea`:**

Recebe entradas de texto com múltiplas linhas.

Atributos:

- *id=""*
- *name=""*
- *rows=""*
- *cols=""*
- *maxlength="" / minlength=""*
- *wrap="off"*: desativa a quebra de linha, pode ser *soft* ou *hard*, pesquisar
- outros como para input: *autocomplete*, *autofocus*, *disabled*, *placeholder*, *readonly*, *form*, *required*.

```jsx
<textarea name="message" id="message" cols="30" rows="10"></textarea>
```

**Tags `select` e `option`:**

Cria um dropdown com opções descritas com a tag `option` usando o atributo *value*.

Atributos:

- *multiple*: permite multiplas escolhas
- *size*: define quantas opções aparecem na lista

```jsx
<label for="listaOpcoes">Qual a opção?</label>
<select name="opcao" id="listaOpcoes">
  <option value="" selected disabled>Selecione uma opção</option>
  <option value="op1">Opção 1</option>
  <option value="op2">Opção 2</option>
  <option value="op3">Opção 3</option>
  <option value="op4">Opção 4</option>
</select>
```

Elemento `optgroup`: cria grupos de opções que podem ser escolhidas, é filho de `select` e pai dos `option`.

```jsx
<label for="listaOpcoes">Qual a opção?</label>
<select name="opcao" id="listaOpcoes"  multiple size="5">
  <option value="" selected disabled>Selecione uma opção</option>
  <optgroup label="Grupo 1">
    <option value="op1">Opção 1</option>
    <option value="op2">Opção 2</option>
    <option value="op3">Opção 3</option>
  </optgroup>
    <optgroup label="Grupo 2">
    <option value="op1">Opção 1</option>
    <option value="op2">Opção 2</option>
    <option value="op3">Opção 3</option>
  </optgroup>
</select>
```
