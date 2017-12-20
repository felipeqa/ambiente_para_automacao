<h1>Arquitetura do projeto</h1>

Configurando seu ambiente usando o gerenciador de pacotes do Windows o "Chocolatey"
-------------------------

  Hj iremos aprender como configurar um ambiente de testes via terminal (tipo apt-get ou brew) com o gerenciador de pacotes do Windows o Chocolatey.

*	para mais informações visite <https://chocolatey.org/>.


<h3>1.Instalando o Chocolatey</h3>
------------------------------------------------------------

*	Abra o cmd como administrador e execute o seguinte comando:

```bash
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

O resultado é:


![Passo 1](readme_images/Picture1.jpg?raw=true)


*	Após a instalação, reinicie o cmd como administrador e digite o seguinte comando:

```bash
choco
```

O resultado é:


![Passo 2](readme_images/Picture2.jpg?raw=true)


<h3>2.Utilizando o Gerenciador de Pacotes </h3>

------------------------------------------------------------


* Agora iremos baixar um terminal que execute comando bash o CMDER, digite no cmd(sempre em modo de administrador) o comando:

```bash
choco install cmder
```

* Confirme com "y" sempre que for solicitado.

O resultado é:


![Passo 3](readme_images/Picture3.jpg?raw=true)


Como podemos ver na imagem abaixo, ele exibe o caminho em que o terminal foi instalado:
'C:\tools\cmder'


![Passo 4](readme_images/Picture4.jpg?raw=true)


<h3>3.Utilizando o CMDER </h3>

*	Feche o CMD e navegue até 'C:\tools\cmder':


![Passo 5](readme_images/Picture5.jpg?raw=true)


* Crie um atalho na sua area de trabalho!
*	Executar o cmder.exe como administrador.


![Passo 6](readme_images/Picture6.jpg?raw=true)


<h3>4.Instalando o Ruby </h3>

* Agora vamos instalar o ruby em nosso ambiente, digite o seguinte comando (não esqueça de estar como administrador):

```bash
choco install ruby
```

* Confirme com "y" sempre que for solicitado.

O resultado é:


![Passo 7](readme_images/Picture7.jpg?raw=true)



* Agora, reinicie o CMDER para ver se foi instalado corretamente digitando:

```bash
ruby --version
```

O resultado é:


![Passo 8](readme_images/Picture8.jpg?raw=true)


<h3>5.Instalando o DevKit </h3>

* Agora vamos instalar o DevKit em nosso ambiente, digite o seguinte comando (não esqueça de estar como administrador):

```bash
choco install ruby2.devkit
```

O resultado é:


![Passo 9](readme_images/Picture9.jpg?raw=true)


Não se preocupe com os Load Errors não afeta a nossa configuração!

<h3>6.Instalando o Chromedriver </h3>

* Agora vamos instalar o chromedriver em nosso ambiente, digite o seguinte comando (não esqueça de estar como administrador):

```bash
choco install chromedriver
```

O resultado é:


![Passo 10](readme_images/Picture10.jpg?raw=true)


Esse driver é o responsavel por gerenciar e abrir o nosso navegador quando executamos os testes!!!

<h3>7.Instalando a gem bundle </h3>

No Console do Cmder, digite o comando:


```bash
gem install bundler
```

Obs:

* Para a instalação de novas gems não é nescessários estar em modo de administrador.
* Modo administrador é utilizado para executar o gerenciador de pacotes "Chocolatey"

Clonando o repositório do git para execução dos teste
------------------------------------------------------

<h3>Selecionando o destino para o clone do projeto</h3>

*	Navegue no Cmder até a pasta em que você achar mais apropriada para ser feito o clone do projeto, como exemplo vou utilizar a pasta projetos dentro de C:.

```bash
cd/
cd projetos
```

<h3>8.Clonando o repositório </h3>

*	No Console do Cmder, digite o comando:

````bash
git clone https://github.com/felipeqa/ambiente_para_automacao.git

````
Como é possível ver, a estrutura do comando é "git clone [endereço do repositório] .

Feito isso, temos um clone do projeto para que possamos trabalhar e executar os testes automatizados.

Automação de Testes
--------------------

Para a automação de testes algumas gems do Ruby são essenciais, sendo elas:
*	Cucumber
*	Capybara
*	Selenium-webdriver

Para manter o controle das Gems usadas no projeto, adicione no arquivo Gemfile e serão instaladas de uma só vez.
Com o arquivo Gemfile configurado, utiliza-se a gem bundler para instalação das dependências listadas:

```bash
cd C:\projetos\ambiente_para_automacao

bundle
```

O resultado é:

![Passo 11](readme_images/Picture11.jpg?raw=true)

Agora vamos executar os testes implementados digitando o comando:

```bash
cucumber
```

Se o teste funcionar corretamente eu vos convido a criar mais cenários com o seu editor de texto preferido (atom, sublime).

* Abra o projeto com o seu editor favorito:
* Abra o arquivo features/specifications/teste.feature
* Adicione mais alguns cenários usando a estrutura:

```bash
  Cenario:
  Dado
  Quando
  Então
```
* Execute o comando:

```bash
cucumber
```

* Copie somente os steps gerados no console, exemplo:

```bash
Dado("que hj é sexta") do
pending # Write code here that turns the phrase above into concrete actions
end

Quando("eu sair do trabalho") do
pending # Write code here that turns the phrase above into concrete actions
end

Então("eu vou estudar automacao de teste") do
pending # Write code here that turns the phrase above into concrete actions
end
```

Implemente os steps e seja feliz! Não deixe de treinar!
Vou deixar aqui alguns códigos do capybara para facilitar o aprendizado!


Capybara Cheatsheet
--------------------

<h4>Navegação</h4>

visit 'https://site.com.br'

<h4>Clique links e botões por id, texto ou nome</h4>

```bash
click_link('id-do-link')
click_link('Texto do Link')
click_link('nome_do_link')
```


<h4>Clica em um botão por id, texto ou nome</h4>

```bash
click_button('id-do-botao')
click_button('Texto do botao')
click_button('nome_do_botao')
```

<h4>Interagindo com Formulários</h4>

```bash
fill_in('nome_do_elemento', :with => 'valor')
choose('nome_do_radio_button')
check('nome_do_checkbox')
uncheck('nome_do_checkbox')
select('opção', :from => 'nome_do_combobox')
```

<h4>Buscar um elemento na página</h4>

```bash
find('#id')
find('.class')
find(:id, 'id_do_elemento')
find(:xpath, 'xpath_do_elemento') find(:css, 'css_do_elemento')
```

<h4>Validações</h4>

```bash
assert_text('texto_que_deve_existir')
assert_no_text('texto_que_não_deve_existir')
has_xpath?('existe_xpath_do_elemento?')
has_css?('existe_css?')
has_content?('existe_conteúdo?')
has_link?(existe_link?')
should have_xpath('deve_existir_xpath_do_elemento')
should have_css('deve_existir_css')
should have_content('deve_existir_conteúdo')
should have_no_content('não_deve_existir_conteúdo')
```


É isso aí pessoal! Espero ter ajudado! Deixarei meus contatos abaixo para qualquer dúvida.

Contato
-------
Estou aberto a sugestões, elogios, críticas ou qualquer outro tipo de comentário.

*	E-mail: felipe_rodriguesx@hotmail.com.br
*	Linkedin: <https://www.linkedin.com/in/luis-felipe-rodrigues-de-oliveira-2b056b5a/>

Licença
-------
Esse código é livre para ser usado dentro dos termos da licença MIT license
