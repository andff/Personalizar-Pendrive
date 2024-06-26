# Personalizar-Pendrive
Personalizar Pendrive (autorun.inf)

https://learn.microsoft.com/pt-br/windows/win32/shell/autorun-cmds?redirectedfrom=MSDN

Entradas autorun.inf
Artigo
13/06/2023
6 colaboradores
Neste artigo
[AutoRun] Chaves
[Conteúdo] Chaves
[ExclusiveContentPaths] Chaves
[IgnoreContentPaths] Chaves
[DeviceInstall] Chaves
Este tópico é uma referência para as entradas que podem ser usadas em um arquivo Autorun.inf. Uma entrada consiste em uma chave e um valor.

[AutoRun] Chaves
action
CustomEvent
ícone
label
open
UseAutoPlay
Shellexecute
Shell
shell\verbo
[Conteúdo] Chaves
[ExclusiveContentPaths] Chaves
[IgnoreContentPaths] Chaves
[DeviceInstall] Chaves
DriverPath
[AutoRun] Chaves
action
CustomEvent
ícone
label
open
UseAutoPlay
Shellexecute
Shell
shell\verbo
ação
A entrada de ação especifica o texto usado na caixa de diálogo Reprodução automática para o manipulador que representa o programa especificado na entrada open ou shellexecute no arquivo Autorun.inf da mídia. O valor pode ser expresso como texto ou como um recurso armazenado em um binário.


Copiar
action=ActionText

Copiar
action=@[filepath\]filename,-resourceID
Parâmetros
ActionText

Texto usado na caixa de diálogo Reprodução automática para o manipulador que representa o programa especificado na entrada aberta ou shellexecute no arquivo Autorun.inf da mídia.

Filepath

Uma cadeia de caracteres que contém o caminho totalmente qualificado do diretório que contém o arquivo binário que contém a cadeia de caracteres. Se nenhum caminho for especificado, o arquivo deverá estar no diretório raiz da unidade.

filename

Uma cadeia de caracteres que contém o nome do arquivo binário.

Resourceid

A ID da cadeia de caracteres dentro do arquivo binário.

Comentários
A chave de ação só é usada no Windows XP Service Pack 2 (SP2) ou posterior. Só há suporte para unidades do tipo DRIVE_REMOVABLE e DRIVE_FIXED. No caso de DRIVE_REMOVABLE, a chave de ação é necessária. Um comando de ação no arquivo Autorun.inf de um CD de áudio ou DVD de filme é ignorado e essas mídias continuam a se comportar como no Windows XP Service Pack 1 (SP1) e anterior.

A cadeia de caracteres exibida na caixa de diálogo Reprodução automática é construída combinando o texto especificado na entrada de ação com texto embutido em código nomeando o provedor, fornecido pelo Shell. O ícone é exibido ao lado dele. Essa entrada sempre aparece como a primeira opção na caixa de diálogo Reprodução automática e é selecionada por padrão. Se o usuário aceitar a opção, o aplicativo especificado pela entrada open ou shellexecute no arquivo Autorun.inf da mídia será iniciado. A opção Sempre fazer a ação selecionada não está disponível nessa situação.

A ação e as teclas de ícone juntas definem a representação do aplicativo que é visto pelo usuário final na caixa de diálogo Reprodução automática. Eles devem ser compostos de forma que os usuários possam identificá-los facilmente. Eles devem indicar o aplicativo a ser executado, a empresa que o criou e qualquer identidade visual associada.

Para compatibilidade com versões anteriores, a entrada de ação é opcional para dispositivos do tipo DRIVE_FIXED. Para esse tipo, uma entrada padrão será usada na caixa de diálogo Reprodução automática se nenhuma entrada de ação estiver presente no arquivo Autorun.inf.

A entrada de ação é obrigatória para dispositivos do tipo DRIVE_REMOVABLE, que até agora não tinham suporte ao Autorun.inf. Se nenhuma entrada de ação estiver presente, a caixa de diálogo Reprodução automática será exibida, mas sem nenhuma opção para iniciar o conteúdo adicional.

CustomEvent
A entrada CustomEvent especifica um evento de conteúdo de Reprodução Automática personalizado.


Copiar
CustomEvent=CustomEventName
Parâmetros
CustomEventName

Uma cadeia de caracteres de texto que contém o nome do evento de conteúdo de Reprodução Automática. O nome não deve ter mais de 100 caracteres alfanuméricos.

Comentários
Você pode incluir um nome de evento personalizado no arquivo Autorun.inf de um volume. Quando a Reprodução Automática solicita que o usuário use um aplicativo com o volume, ele exibe apenas os aplicativos que se registraram para o nome do evento personalizado especificado. Para obter informações sobre como você pode registrar um aplicativo como um manipulador para seu evento de conteúdo de Reprodução Automática personalizado, consulte Inicialização automática com Reprodução Automática ou Como Registrar um Manipulador de Eventos.

O exemplo a seguir especifica o valor "MyContentOnArrival" como um novo evento de conteúdo de Reprodução Automática.


Copiar
CustomEvent=MyContentOnArrival
ícone
A entrada de ícone especifica um ícone que representa a unidade habilitada para AutoRun na interface do usuário do Windows.


Copiar
icon=iconfilename[,index]
Parâmetros
iconfilename

Nome de um arquivo .ico, .bmp, .exe ou .dll que contém as informações do ícone. Se um arquivo contiver mais de um ícone, você também deverá especificar o índice baseado em zero do ícone.

Comentários
O ícone, juntamente com o rótulo, representa a unidade habilitada para AutoRun na interface do usuário do Windows. Por exemplo, no Windows Explorer, a unidade é representada por esse ícone em vez do ícone de unidade padrão. O arquivo do ícone deve estar no mesmo diretório que o arquivo especificado pelo comando open .

O exemplo a seguir especifica o segundo ícone no arquivo MyProg.exe.


Copiar
icon=MyProg.exe,1
label
A entrada de rótulo especifica um rótulo de texto que representa a unidade habilitada para AutoRun na interface do usuário do Windows.


Copiar
label=LabelText
Parâmetros
Labeltext

Uma cadeia de caracteres de texto que contém o rótulo. Ele pode conter espaços e não deve ter mais de 32 caracteres.

 Observação

É possível colocar um valor no parâmetro LabelText que excede 32 caracteres e não recebe nenhuma mensagem de erro. No entanto, o sistema exibe apenas os primeiros 32 caracteres. Todos os caracteres após o 32º são truncados e não são exibidos. Por exemplo, se o LabelText for o seguinte: label="Este CD foi projetado para ser o CD de música final". O seguinte será exibido: "Este CD foi projetado para ser o ul".

 

Comentários
O rótulo, juntamente com um ícone, representa a unidade habilitada para AutoRun na interface do usuário do Windows.

O exemplo a seguir especifica o valor "My Drive Label" como o rótulo da unidade.


Copiar
label=My Drive Label
Abrir
A entrada aberta especifica o caminho e o nome do arquivo do aplicativo que a Execução Automática inicia quando um usuário insere um disco na unidade.


Copiar
open=[exepath\]exefile [param1 [param2] ...] 
Parâmetros
exefile

Caminho totalmente qualificado de um arquivo executável que é executado quando o CD é inserido. Se apenas um nome de arquivo for especificado, ele deverá estar no diretório raiz da unidade. Para localizar o arquivo em um subdiretório, você deve especificar um caminho. Você também pode incluir um ou mais parâmetros de linha de comando para passar para o aplicativo de inicialização.

UseAutoPlay
No Windows XP, a entrada UseAutoPlay especifica que a Reprodução Automática deve ser usada em vez de Executar Automaticamente.

No Windows Vista e posteriores, essa entrada faz com que todas as ações especificadas para AutoRun (usando as entradas abertas ou shellexecute ) sejam suprimidas da caixa de diálogo Reprodução Automática. Essa entrada não tem efeito em versões do Windows anteriores ao Windows XP.

Em Windows 8 e posteriores, especificar um valor de 0 desabilitará a reprodução automática para este dispositivo.

Parâmetros
Para usar essa opção, adicione uma entrada para UseAutoPlay ao arquivo Autorun.inf e defina a entrada como 1. Nenhum outro valor tem suporte em versões do Windows anteriores a Windows 8.

Em Windows 8 e posterior, especifique um valor de 0 para desabilitar a reprodução automática para este dispositivo.


Copiar
UseAutoPlay=1
Comentários
Atualmente, UseAutoPlay é aplicável somente no Windows XP ou posterior e somente em uma unidade que GetDriveType determina ser do tipo DRIVE_CDROM.

Quando UseAutoPlay é usado, qualquer ação especificada pelas entradas open ou shellexecute em Autorun.inf é ignorada no Windows XP e omitida da caixa de diálogo Reprodução Automática no Windows Vista.

A Execução Automática normalmente é usada para executar ou carregar automaticamente algo contido na mídia inserida, enquanto a Reprodução Automática apresenta uma caixa de diálogo que inclui uma lista de ações relevantes que podem ser executadas e permite que o usuário escolha qual ação tomar. Para obter mais informações sobre a diferença entre a Execução Automática e a Reprodução Automática, consulte Criando um aplicativo CD-ROM habilitado para Execução Automática e Usando e Configurando a Reprodução Automática, respectivamente.

Exemplo de uso
Um CD contém três arquivos: Autorun.inf, Readme.txt e Music.wma. Dependendo da versão do Windows em uso e das opções especificadas em Autorun.inf, o CD pode ser manipulado por AutoRun ou AutoPlay quando ele é inserido (supondo que AutoRun/AutoPlay esteja habilitado para a unidade na qual o CD está inserido).

Primeiro, considere um arquivo Autorun.inf com o seguinte conteúdo, observando que UseAutoPlay=1 não está especificado:


Copiar
[AutoRun]
shellexecute="Readme.txt"
A ação executada pelo Shell quando este CD é inserido depende da versão do Windows em uso:

No Windows XP ou anterior, esse CD é tratado pela Execução Automática quando é inserido. Nesse caso, a entrada shellexecute é lida e o Shell invoca o manipulador de arquivos associado a arquivos .txt; normalmente, isso abriria Readme.txt no Bloco de Notas.
No Windows Vista, a presença de um arquivo Autorun.inf com uma entrada shellexecute faz com que a mídia seja identificada como tipo de Reprodução Automática "Software e jogos". Nesse caso, o usuário recebe uma caixa de diálogo Reprodução Automática que inclui a ação especificada pela entrada shellexecute (apresentada como "Carregar Readme.txt" na caixa de diálogo), juntamente com ações padrão associadas à mídia do tipo "Software e jogos".
Para indicar que a Reprodução Automática deve ser usada em vez de Executar Automaticamente no Windows XP e que a ação especificada pela entrada shellexecute de Execução Automática deve ser suprimida da caixa de diálogo Reprodução Automática no Windows Vista, insira UseAutoPlay no arquivo Autorun.inf da seguinte maneira:


Copiar
[AutoRun]
shellexecute="Readme.txt"
UseAutoPlay=1
Mais uma vez, a ação executada pelo Shell quando este CD é inserido depende da versão do Windows em uso.

Em versões do Windows anteriores ao Windows XP, a Execução Automática ainda é usada e a ação especificada por shellexecute é executada, conforme descrito anteriormente. (Observe que somente a Execução Automática está disponível em versões do Windows anteriores ao Windows XP.)
No Windows XP, a entrada UseAutoPlay faz com que a Reprodução Automática seja usada no lugar de AutoRun. Nesse caso, a Reprodução Automática determina que a mídia contém um arquivo de Áudio do Windows Media (.wma) e categoriza o conteúdo como "Arquivos de música". O usuário recebe uma caixa de diálogo Reprodução Automática que contém manipuladores registrados para o tipo de mídia "Arquivos de música" Reprodução Automática; a entrada shellexecute de Execução Automática é ignorada.
Shellexecute
Versão 5.0. A entrada shellexecute especifica um aplicativo ou arquivo de dados que a AutoRun usará para chamar ShellExecuteEx.


Copiar
shellexecute=[filepath\]filename[param1, [param2]...] 
Parâmetros
Filepath

Uma cadeia de caracteres que contém o caminho totalmente qualificado do diretório que contém os dados ou o arquivo executável. Se nenhum caminho for especificado, o arquivo deverá estar no diretório raiz da unidade.

filename

Uma cadeia de caracteres que contém o nome do arquivo. Se for um arquivo executável, ele será iniciado. Se for um arquivo de dados, ele deverá ser um membro de um tipo de arquivo. ShellExecuteEx inicia o comando padrão associado ao tipo de arquivo.

paramx

Contém parâmetros adicionais que devem ser passados para ShellExecuteEx.

Comentários
Essa entrada é semelhante a aberta, mas permite que você use informações de associação de arquivo para executar o aplicativo.

shell
A entrada do shell especifica um comando padrão para o menu de atalho da unidade.


Copiar
shell=verb
Parâmetros
verbo

O verbo que corresponde ao comando de menu. O verbo e seu comando de menu associado devem ser definidos no arquivo Autorun.inf com uma entrada shell\verb .

Comentários
Quando um usuário clica com o botão direito do mouse no ícone de unidade, um menu de atalho é exibido. Se um arquivo Autorun.inf estiver presente, o comando de menu de atalho padrão será retirado dele. Esse comando também é executado quando o usuário clica duas vezes no ícone da unidade.

Para especificar o comando de menu de atalho padrão, primeiro defina o verbo, a cadeia de caracteres de comando e o texto do menu com shell\verbo. Em seguida, use o shell para torná-lo o comando de menu de atalho padrão. Caso contrário, o texto do item de menu padrão será "Reprodução Automática", que inicia o aplicativo especificado pela entrada aberta .

shell\verbo
A entrada shell\verb adiciona um comando personalizado ao menu de atalho da unidade.


Copiar
shell\verb\command=Filename.exe 
shell\verb=MenuText
Parâmetros
verbo

O verbo do comando de menu. A entrada shell\verb\command associa o verbo a um arquivo executável. Os verbos não devem conter espaços inseridos. Por padrão, verbo é o texto exibido no menu de atalho.

Filename.exe

O caminho e o nome do arquivo do aplicativo que executa a ação.

Menutext

Esse parâmetro especifica o texto exibido no menu de atalho. Se for omitido, o verbo será exibido. MenuText pode ser misto de maiúsculas e minúsculas e pode conter espaços. Você pode definir uma tecla de atalho para o item de menu colocando um e comercial (&) na frente da letra.

Comentários
Quando um usuário clica com o botão direito do mouse no ícone de unidade, um menu de atalho é exibido. Adicionar entradas de shell\verbo ao arquivo Autorun.inf da unidade permite adicionar comandos a esse menu de atalho.

Há duas partes nessa entrada, que devem estar em linhas separadas. A primeira parte é shell\verb\command. É obrigatório. Ele associa uma cadeia de caracteres, chamada de verbo, ao aplicativo a ser iniciado quando o comando é executado. A segunda parte é a entrada de verbo **shell\**. É opcional. Você pode incluí-lo para especificar o texto exibido no menu de atalho.

Para especificar um comando de menu de atalho padrão, defina o verbo com shell\verbo e torne-o o comando padrão com a entrada do shell .

O fragmento autorun.inf de exemplo a seguir associa o verbo readit à cadeia de caracteres de comando "Bloco de notas abc\readme.txt". O texto do menu é "Leia-me" e 'M' é definido como a tecla de atalho do item. Quando o usuário seleciona esse comando, o arquivo abc\readme.txt da unidade é aberto com o Bloco de Notas da Microsoft.


Copiar
shell\readit\command=notepad abc\readme.txt 
shell\readit=Read &Me
[Conteúdo] Chaves
Há três teclas de tipo de arquivo: MusicFiles, PictureFiles e VideoFiles.

Se um desses conteúdos for definido como true por meio de um dos valores que não diferenciam maiúsculas de minúsculas 1, y, sim, t ou true, a interface do usuário de reprodução automática exibirá os manipuladores associados a esse tipo de conteúdo, independentemente de o conteúdo desse tipo existir na mídia.

Se um desses conteúdos for definido como false por meio de um dos valores que não diferenciam maiúsculas de minúsculas 0, n, não, f ou false, a interface do usuário de reprodução automática não exibirá os manipuladores associados a esse tipo de conteúdo, mesmo que o conteúdo desse tipo seja detectado na mídia.

O uso desta seção destina-se a permitir que os autores de conteúdo comuniquem a intenção do conteúdo para a Reprodução automática. Por exemplo, um CD pode ser categorizado como contendo apenas conteúdo de música, embora também tenha imagens e vídeos e, de outra forma, seria visto como tendo conteúdo misto.

A seção [Conteúdo] só tem suporte no Windows Vista e posterior.


Copiar
[Content]
MusicFiles=Y
PictureFiles=0
VideoFiles=false
[ExclusiveContentPaths] Chaves
As pastas listadas nesta seção limitam a reprodução automática a pesquisar apenas essas pastas e suas subpastas em busca de conteúdo. Eles podem ser fornecidos com ou sem uma barra invertida à esquerda (\). Em ambos os casos, eles são tomados como caminhos absolutos do diretório raiz da mídia. No caso de pastas com espaços em seus nomes, não coloque-as entre aspas, pois as aspas são tomadas literalmente como parte do caminho.

O uso desta seção destina-se a permitir que os autores de conteúdo comuniquem a intenção do conteúdo para a Reprodução automática e reduzam o tempo de verificação limitando a verificação a determinadas áreas significativas da mídia.

Veja a seguir todos os caminhos válidos


Copiar
[ExclusiveContentPaths]
\music
\music\more music
music2
A seção [ExclusiveContentPaths] só tem suporte no Windows Vista e posterior.

[IgnoreContentPaths] Chaves
As pastas listadas nesta seção e suas subpastas são ignoradas pela Reprodução automática ao pesquisar conteúdo em uma mídia. Eles podem ser fornecidos com ou sem uma barra invertida à esquerda (\). Em ambos os casos, eles são tomados como caminhos absolutos do diretório raiz da mídia. No caso de pastas com espaços em seus nomes, não coloque-as entre aspas, pois as aspas são tomadas literalmente como parte do caminho.

Os caminhos nesta seção têm precedência sobre caminhos na seção [ExclusiveContentPaths] . Se um caminho fornecido em [IgnoreContentPaths] for uma subpasta de um caminho fornecido em [ExclusiveContentPaths], ele ainda será ignorado.

O uso desta seção destina-se a permitir que os autores de conteúdo comuniquem a intenção do conteúdo para a Reprodução automática e reduzam o tempo de verificação limitando a verificação a determinadas áreas significativas da mídia.

Veja a seguir todos os caminhos válidos


Copiar
[IgnoreContentPaths]
\music
\music\more music
music2
A seção [IgnoreContentPaths] só tem suporte no Windows Vista e posterior.

[DeviceInstall] Chaves
DriverPath
A entrada DriverPath especifica um diretório a ser pesquisado recursivamente em busca de arquivos de driver. Esse comando é usado durante uma instalação do driver e não faz parte de uma operação de Execução Automática. A seção [DeviceInstall] só tem suporte no Windows XP.


Copiar
[DeviceInstall]
DriverPath=directorypath
Parâmetros
Directorypath

Um caminho para um diretório que o Windows pesquisa arquivos de driver, juntamente com todos os seus subdiretórios.

Comentários
Não use letras de unidade no directorypath , pois elas mudam de um computador para o outro.

Para pesquisar vários diretórios, adicione uma entrada DriverPath para cada diretório como neste exemplo.


Copiar
[DeviceInstall]
DriverPath=drivers\video 
DriverPath=drivers\audio
Se nenhuma entrada driverPath for fornecida na seção [DeviceInstall] ou a entrada DriverPath não tiver nenhum valor, essa unidade será ignorada durante uma pesquisa de arquivos de driver.
