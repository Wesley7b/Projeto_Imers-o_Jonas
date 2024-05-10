# Projeto_Imers-o_Jonas
# SOS CUFA PARA RS

A CUFA intensifica sua mobilização solidária em apoio ao Rio Grande do Sul, que foi duramente atingido pelas chuvas, deixando famílias 
desabrigadas e em necessidade urgente de alimentos,água,produtos de higiene e limpeza, cobertores, colchões . 
A organização já realizou doações de materiais de limpeza, água e cestas básicas, mas destaca que a necessidade persiste ainda a muitas famílias 
desabrigadas e desaparecidas. O Rio Grande do Sul vive um momento de profunda tristeza e desolação após as devastadoras enchentes que atingiram o estado nos últimos dias. As chuvas incessantes causaram inundações, deslizamentos de terra e outros estragos, deixando um rastro de destruição e sofrimento por onde passaram,Cidades submersas e milhares de desalojados.

#Doações financeiras:
doacoespaypal@cufa.org.br
doacoes@cufa.org.br
* **Banco de Alimentos do Rio Grande do Sul:** https://www.bandars.com.br/![cufa sos](https://github.com/Wesley7b/Projeto_Imersao_Jonas/assets/169486083/d39e47df-2348-4f0b-87f5-f1407c0f0b81)

* **Cruz Vermelha Brasileira:** https://www.cruzvermelha.org.br/doacoes/
* **Cáritas Brasileira:** https://www.caritas.org.br/

    # Atalhos do SOS Rio Grande do SUL CUFA

# SOS RS CUFA
def doacao_alimentos(tipo_alimento, quantidade, localizacao):
  # SOS ponto de coleta
  ponto_coleta = "Rua Exemplo, 7 - Centro"
  resposta = f"Obrigado pela sua doação de {quantidade} de {tipo_alimento}! O ponto de coleta mais próximo de {localizacao} é {ponto_coleta}."
  return resposta

def buscar_alimentos(necessidades, localizacao):
  # SOS por alimentos
  alimentos_disponiveis = "Cestas básicas com arroz, feijão, macarrão e alimentos enlatados."
  resposta = f"Em {localizacao}, temos disponíveis {alimentos_disponiveis}."
  return resposta

def inf_apoioenchentes_rs():
  mensagem = """
  A CUFA conta com o apoio: GOLLOG, iFood, Unilever. Mercado Livre; Grupo Elfa; AES.
  A Campanha de ajuda para as Famílias do Rio Grande do Sul segue e se você estiver fora do país, também pode ajudar pelo pix:
doacoespaypal@cufa.org.br e Para doações: doacoes@cufa.org.br
É hora de unirmos forças para construir um futuro mais justo e digno para todos.
Cada doação conta! Juntos, podemos fazer a diferença e trazer esperança para quem mais precisa. 💪🏾:
  """
  return mensagem

#IA Chat DATA

prompt = "Olá! Ficamos felizes em saber que você está disposto(a) a ajudar o povo do RS!focado em combater a fome, a insegurança alimentar e te atualizar sobre a tragedia de enchetes do Rio grande do sul. Como posso te ajudar?"
chat = model.start_chat(history=[])
response = chat.send_message(prompt)
print("Chatbot:", response.text, '\n')

while True:
 prompt = input('Você: ')
 if prompt.lower() == "fim":
   break

  # Escolha do usuário
 if any(palavra in prompt.lower() for palavra in ["insegurança", "alimentar", "fome"]):
    response = chat.send_message(info_inseguranca_alimentar())
 elif any(palavra in prompt.lower() for palavra in ["enchente", "rs", "rio grande do sul", "ajuda"]):
    response = chat.send_message(info_enchentes_rs())
  # Identificação da intenção do usuário
 elif "doar" in prompt.lower():
    # Extrair informações da doação
    tipo_alimento = "alimentos"
    quantidade = "alguns"
    localizacao = "sua região"
    response = chat.send_message(doacao_alimentos(tipo_alimento, quantidade, localizacao))
 elif "buscar" in prompt.lower():
    # Extrair informações da busca
    necessidades = "alimentos"
    localizacao = "sua região"
    response = chat.send_message(buscar_alimentos(necessidades, localizacao))
 else:
    response = chat.send_message(prompt)
 
 print("Chatbot:", response.text, '\n')
