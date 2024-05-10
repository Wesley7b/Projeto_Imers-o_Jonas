# Projeto_Imers-o_Jonas
# Inicializando o Sistema

!pip install -q -U google-generativeai

import google.generativeai as genai
from google.colab import userdata
api_key = userdata.get('Key_Secret')
genai.configure(api_key=api_key)

Generation_config = {
    'candidate_count': 1,
    'temperature': 0.7,
}

safety_settings = {  
    'HARASSMENT': 'BLOCK_NONE',
    'HATE': 'BLOCK_NONE',
    'SEXUAL': 'BLOCK_NONE',
    'DANGEROUS': 'BLOCK_NONE',
}

model = genai.GenerativeModel(model_name='gemini-1.0-pro',
                                  generation_config=Generation_config,
                                  safety_settings=safety_settings)

#Melhorando a visualização
import textwrap
from IPython.display import display
from IPython.display import Markdown

def to_markwown(text):
  text = text.replace(' * '  ' * ')
  return Markdown(textwrap.indent(text, '> ', predicate=lambda _: True))
  #Imprimindo o histórico
  for message in chat.history:
    display(to_markwown(f'**{message.role}**:{message.parts[0].text}'))
    print*('--------------------------------------------')

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
