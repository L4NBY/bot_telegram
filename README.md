# bot_telegram


Bot telegram converter texto para áudio 

```
@bot.message_handler(commands=['audio' , 'áudio' , 'AUDIO' , 'ÁUDIO'])
def audio_0(mensagem):
    
    audio = mensagem.text.lstrip('/áudio').lstrip('/audio').lstrip('/ÁUDIO'). lstrip('/AUDIO'). lstrip()
    
    arquivo = open('bot.txt', 'w+')
    print(audio ,file=arquivo)

    arquivo.close()
    with open ('bot.txt' , 'r') as bot_audio:
        try:
            for lih in bot_audio:
                frase_1 = gtts.gTTS(lih , lang='pt-br')
                frase_1.save('bot_audio_lanby.mp3')
                
                bot.send_message(mensagem.chat.id , 'GERANDO O AUDIO ....')
                audio_feito = open('bot_audio_lanby.mp3' , 'rb')
                bot.send_audio(mensagem.chat.id , audio_feito)
        except:
            bot.send_message(mensagem.chat.id , 'EXEMPLO /audio ola tudo bem ADM ')
```
