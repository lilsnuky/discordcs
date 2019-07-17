

<div style="text-align: center; margin: 0 auto;">
  <center><img src="https://imgur.com/Fl8oQGB.png" width="auto" /></center></div>
<div><center><a href="https://nodei.co/npm/discordcs/"><img src="https://nodei.co/npm-dl/discordcs.png"></a></div>



## Sobre o projeto
O DiscordCS é uma biblioteca de suporte para discord.js feita com o intuito de te ajudar a desenvolver um projeto de uma forma estruturada e mais simples para aqueles que não possuem uma vasta experiência na área de desenvolvimento de bots, desenvolvido em Node.js, ele traz essa simplicidade para os usuários criarem suas aplicações de uma forma mais rápida e ao mesmo tempo bem estruturada, ela também foi feita para aqueles que já possuem uma vasta experiência com desenvolvimento e sabe fazer algo complexo e bem estruturado.

- Biblioteca orientada a objetos.
- Estrutura de dados.
- Totalmente configurada.

## Instalando a biblioteca
*[OBS]* **Compatível apenas com as versões discord.js v11.5 pra cima.**  
*[OBS - 2]* *Nas futuras atualizações da DiscordCS, ela será totalmente dependente da lib *discord.js*

É aconselhável que você instale a biblioteca *discord.js*, pois dependendo dos updates da biblioteca em si, isso pode gerar alguns erros, então é totalmente recomendado que seja instalado para a lib não vir com erros (mas caso você queira instalar apenas o DiscordCS, ele irá vir com a versão no qual ele foi desenvolvida, e com total certeza que nos updates futuros irei atualizar suas versões na *package.json*).
- Digite este comando: `npm install discord.js --save` (e dê enter)
- E então digite novamente: `npm install discordCS --save` (e dê enter)

### Como funciona? 
Após você instalar a biblioteca, é preciso saber de todas as suas funções. Ela vem com uma mala repleta e diversificada, fique com alguns exemplos abaixo:
  - Parâmetros: Os parâmetros devem ser apresentados, são palavras chaves e cada um retorna um dado especifico.
    - `{member}`: Retorna o @mention do autor que executou o comando.
    - `{member.tag}`: Retorna o username + discriminator do autor que executou o comando.
    - `{member.id}`: Retorna o ID do autor que executou o comando.
    - `{guild}`: Retorna o ID e o nome da guilda na qual o comando foi executado.
    - `{guild.id}`: Retorna o ID da guilda na qual o comando foi executado.
    - `{guild.name}`: Retorna o nome da guilda na qual o comando foi executado.
    - `{err}`: Retorna o erro.
    - `{permissions}: Retorna as permissões necessárias para executar o comando.`

  - Funções / Instâncias
    - `Client(options)`: Instância responsável por dar início ao bot e configurá-lo.

      -`options.token`: Informar o token de sua aplicação. (Obrigatório)
      -`options.prefixes`: Informar o prefixo do seu bot (em breve terá como adicionar em array). (Obrigatório)
      - `options.guilds`: Caso você queira que sua aplicação seja exclusiva para algumas guildas, adicione a ID da guilda (caso ao contrário precisa ser em array / caso seja mais de um é obrigatório ser em array).
      - `options.cooldown`: Configurar o cooldown de sua aplicação.
          - `cooldown.set`: Definir true/false se o cooldown deve ser ativado.
          - `cooldown.time`: Definir tempo em segundos do cooldown.
          - `cooldown.msg`: Definir a mensagem do cooldown.
      - `options.owners`: Definir os ID's dos desenvolvedores do bot. (Array/ String)
      - `options.description`: Definir a descrição de sua aplicação.
      - `options.readylib`: Definir true/false se deve aparecer ready padrão da lib.
      - `options.logs`: Definir true/false se deve aparecer as atividades da lib.
      - `options.messagesWarn`: Definir as mensagens de aviso.
          - `messagesWarn.hasPermission`: Definir a mensagem que o membro não possui a permissão necessária.
          - `messagesWarn.botPermission`: Definir a mensagem que o bot não possui a permissão.
          - `messagesWarn.err`: Definir mensagem de avisar quando ocorre erro na aplicação.
      - `options.mentionBot`: Fazer o bot responder assim que quando for mencionado.
          - `mentionBot.rest`: Definir true/false para ver se ele pode responder a um comando.
          - `mentionBot.message`: Personalizar a mensagem que ele vai enviar para o usuário que for mencioná-lo.

      - `Client.CommandsRegister.registerCommands(__dirname+"/./caminho)`: definir aonde fica a pasta dos comandos.

    - `Command(client, info)`: Instância responsável por estruturar o comando do bot

        - `info.command`: Nome do comando. (Obrigatório)
        - `info.aliases`: Nomes alternativos para este comando.
        - `info.description`: Descrição do comando.
        - `info.isOwner`: Se o comando é permitido somente para desenvolvedores (true/false)
        - `info.permissions`: Permissões do comando.
          - `permissions.bot`: Permissão que o bot precisa para executar este comando.
          - `permissions.member`: Permissão que o membro precisa para executar este comando.

## Exemplo de como utilizar
  - Iniciar/run o bot
      ```js
      const DiscordCS = require('discordcs')
      const client = new DiscordCS.Client({
        token: 'token do bot',
        prefixes: 'prefixo do bot',
        readylib: false
      })

      client.on('ready', () =>{
        console.log('iniciado com sucesso')
        client.CommandsRegister.registerCommands(__dirname+'/./caminho_command')
      })
      ```
  - Iniciar um comando
    ```js
    const {Command} = require('discordcs')
        class ping extends Command{
            constructor(client){
                super(client,{
                    command: 'ping',
                    aliases: ['p'],
                    description: 'ping pong',
                })
                this.client = client
            }

          async startCommand(message, args){
                message.channel.send('pong! '+ Math.round(this.client.ping))
            }
        }
        module.exports = ping
    ```
## Pull Requests
Como eu estou sem tempo, eu decidi postar uma parte deste projeto que eu pretendo focar (se vocês curtirem a idéia ele terá updates com funções novas e algumas novidades). Por enquanto aqui vai estar uma explicação bem resumida de como utilizar esta biblioteca pois como eu disse, eu ando sem tempo. As explicações serão mantidas aqui até eu conseguir desenvolver um site com mais informações sobre a biblioteca. Segue abaixo as Pull Requests:

  - Como eu sou uma pessoa só, preciso da força de vocês para que eu possa melhorar meu projeto, caso você tenha interesse em melhora-lo, maravilha! Siga as instruções a seguir para enviar aquele Pull Request TOP de linha. Ele precisará ter:
    * Código estruturado utilizando classes e métodos.
    * Código bem comentado, para que eu possa entender melhor sua estrutura e seu todo.
    * Variáveis em inglês e que sejam bem claras sobre o que elas fazem. (Isso necessita de um bom conhecimento sobre inglês).
    * Comentar na hora de dar seu Pull Request, opinando o porque seu código melhoraria na biblioteca e quais são suas vantagens.
## Links
* [Franklin Bot](https://discordapp.com/oauth2/authorize?client_id=500473582980300801&scope=bot&permissions=8)
* [Servidor oficial de suporte da DiscordCS](ad_mail Link permanente do servidor:
https://discord.gg/h4A2yKZ)

## Avisos
Este projeto está em fase de testes, então alguns bugs podem ocorrer. Caso você queria suporte/ajuda com pessoas que entendam sobre a biblioteca, entre no nosso servidor oficial do Discord listado na parte Links.
