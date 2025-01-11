# Phishing para captura de senhas do Facebook

### Ferramentas

- Kali Linux
- setoolkit

### Configurando o Phishing no Kali Linux

- Acesso root: ``` sudo su ```
- Iniciando o setoolkit: ``` setoolkit ```
- Tipo de ataque: ``` Social-Engineering Attacks ```
- Vetor de ataque: ``` Web Site Attack Vectors ```
- Método de ataque: ```Credential Harvester Attack Method ```
- Método de ataque: ``` Site Cloner ```
- Obtendo o endereço da máquina: ``` ifconfig ```
- URL para clone: http://www.facebook.com

### Resutados (antes da correção de vulnerabilidades)

![Alt text](./passwd.png "Optional title")

### Explicação

- Apesar de conseguir clonar a página corretamente, nos testes realizados, verificou-se que o Facebook possui uma proteção contra scripts maliciosos e captura de credenciais. Nos testes mais recentes, é possível observar o seguinte log no setoolkit:
![logkali](https://github.com/user-attachments/assets/24c04cca-cab5-47ec-90c7-4aff1db1871f)

O log indica que o ataque foi parcialmente bem-sucedido, porém as credenciais ainda não foram capturadas de forma clara.

### Explicação dos resultados

- POST Request:

- A solicitação POST que aparece no log é do tipo ajax, o que pode indicar que o formulário está sendo enviado de maneira assíncrona através de uma requisição AJAX. Isso pode dificultar a captura de credenciais, pois não há uma submissão direta do formulário na página.
Mensagem de Sucesso (WE GOT A HIT):

- A linha [*] WE GOT A HIT! Printing the output: significa que o SEToolkit encontrou algo relevante, o que é um bom sinal de que ele identificou algum campo de entrada, provavelmente o campo de username ou algo relacionado ao login.
POSSIBLE USERNAME FIELD FOUND:

- A menção de POSSIBLE USERNAME FIELD FOUND indica que o SEToolkit encontrou um campo que pode ser o de nome de usuário, mas os dados exatos de credenciais (como username ou password) não estão sendo extraídos diretamente.

### Alternativa contra a defesa

 - Uma possibilidade de resolução, está no próprio ``` setoolkit ``` onde se pode realizar ``` Custon Import ``` . Ainda na opção ``` 3) Credential Harvester Attack Method ```, ao invés do ``` Site cloner ```, vamos utilizar a opção ``` 3) Custom Import ```. Que irá nos possibilitar utilizar um arquivo modificado da página oficial do Facebook:

![setoolkit](https://github.com/user-attachments/assets/f057e1b1-4d99-437d-9ee5-7073b3c00f73)

## Criando um arquivo

- Crie um arquivo ``` index.html ``` no diretório de sua preferência

![index](https://github.com/user-attachments/assets/7b271428-9836-4c22-812d-6b7677d360ed)


## Copiando código fonte

- Acesse o site oficial do Facebook (https://www.facebook.com/), abra código fonte da página e copie todo o seu conteúdo:

![facebookpage](https://github.com/user-attachments/assets/69635ae6-304e-41c2-bb79-6482e60e9093)
![sourcecode](https://github.com/user-attachments/assets/bfd40b23-d05a-40f3-baa4-a06f5a2e9f1e)
![copysource](https://github.com/user-attachments/assets/1b0d04fd-9840-464d-b1c3-764f918ac373)


## Editando arquivo

- Vá até o diretório onde foi salvo o arquivo ``` index.html ``` e cole código fonte copiado. Você pode editá-lo com o "Mousepad":

![indexedit](https://github.com/user-attachments/assets/6a0043f4-0218-4121-88a6-8e0bfe11b244)

- Localize a linha "<script src="https://static.xx.fbcdn.net/rsrc.php/v4/y8/r/Qo04Jy8d4P6.js" data-bootloader-hash="lp6Cw4s" crossorigin="anonymous"></script>" e apague-a. Ela que está associada ao botão de ``` Log in ``` do Facebook. Excluindo-a, iremos fazer um bypass na etapa de verificação do Facebook, que nos impediu de obter as credenciais anteriormente.

![buttonline](https://github.com/user-attachments/assets/b3286591-5a14-49aa-b6f2-adc05e958655)

- Após excluir, lembre-se de salvar o arquivo


### Testando o bypass

- Ainda seguindo as etapas anteriores: ``` 1) Social-Engineering Attacks ``` - ``` 2) Web Site Attack Vectors ``` - ``` 3) Credential Harvester Attack Method ```, vamos usar a opção ``` Custon Import ```  ao invés do ``` Site Cloner ```. Nele iremos especificar o caminho do diretório que criamos e editamos o arquivo ``` index.html ```.
- Em ``` Path to the website to be cloned ``` cole o caminho do diretório e de ``` [enter] ```. Repita o mesmo para ``` URL of the website you imported ```.

![filepath](https://github.com/user-attachments/assets/d3e48ae0-ac7e-4eb8-89f5-28bb55ab7d95)

### Capturando acessos e credenciais

- No navegador de qualquer dispositivo de sua rede, navegue até o IP do servidor que contem o clone da página. Verifique que ele exibe um log no ``` toolkit ```, contendo o IP, data e hora de acesso do dispositivo:
![log](https://github.com/user-attachments/assets/f4f6c222-fe3c-48a2-a468-2290c56b2e74)











