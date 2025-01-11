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

### Resutados

![Alt text](./passwd.png "Optional title")

### Explicação

- Apesar de conseguir clonar a página corretamente, nos testes realizados, verificou-se que o Facebook possui uma proteção contra scripts maliciosos e captura de credenciais. Nos testes mais recentes, é possível observar o seguinte log no setoolkit:
![log1 dio](https://github.com/user-attachments/assets/49070669-4f6d-44e4-8ebd-00d26049c2ff)
O log indica que o ataque foi parcialmente bem-sucedido, porém as credenciais ainda não foram capturadas de forma clara.

## Explicação dos resultados

- POST Request:

- A solicitação POST que aparece no log é do tipo ajax, o que pode indicar que o formulário está sendo enviado de maneira assíncrona através de uma requisição AJAX. Isso pode dificultar a captura de credenciais, pois não há uma submissão direta do formulário na página.
Mensagem de Sucesso (WE GOT A HIT):

- A linha [*] WE GOT A HIT! Printing the output: significa que o SEToolkit encontrou algo relevante, o que é um bom sinal de que ele identificou algum campo de entrada, provavelmente o campo de username ou algo relacionado ao login.
POSSIBLE USERNAME FIELD FOUND:

- A menção de POSSIBLE USERNAME FIELD FOUND indica que o SEToolkit encontrou um campo que pode ser o de nome de usuário, mas os dados exatos de credenciais (como username ou password) não estão sendo extraídos diretamente.

### Alternativa contra a defesa

 - Uma possibilidade de resolução, está no próprio ``` setoolkit ``` onde se pode realizar ``` Custon Import ``` . Ainda na opção ``` 3) Credential Harvester Attack Method ```, ao invés do ``` Site cloner ```, vamos utilizar a opção ``` 3) Custom Import ```. Que irá nos possibilitar utilizar um arquivo modificado da página oficial do Facebook:

![setoolkit](https://github.com/user-attachments/assets/d7234bda-7dd9-47cb-9d65-f514cfbec4dd)

## Criando um arquivo

- Crie um arquivo ``` index.html ``` no diretório de sua preferência

![index](https://github.com/user-attachments/assets/7b271428-9836-4c22-812d-6b7677d360ed)


## Salvar página

- Acesse o site oficial do Facebook (https://www.facebook.com/), abra código fonte da página e copie todo o seu conteúdo:

![facebookpage](https://github.com/user-attachments/assets/6a077533-2ab5-4bd3-b39f-4973b3a670e7)
![sourcecode](https://github.com/user-attachments/assets/727abbf8-908e-4df7-a633-eb51edad9a9b)
![copysource](https://github.com/user-attachments/assets/f9962c5e-ba3f-42a8-9fb6-8f5d544d355b)

- Vá até o diretório onde foi salvo o arquivo ``` index.html ``` e cole código fonte copiado. Você pode editá-lo com o "Mousepad":

![indexedit](https://github.com/user-attachments/assets/6a0043f4-0218-4121-88a6-8e0bfe11b244)


