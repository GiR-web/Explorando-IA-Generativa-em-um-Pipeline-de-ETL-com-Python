## Explorando-IA-Generativa-em-um-Pipeline-de-ETL-com-Python

📰 Geração de Notícias Personalizadas

Script Python para criar mensagens personalizadas para usuários a partir de IDs em CSV.

✨ Funcionalidades

📄 Leitura de IDs de usuários de userID.csv com pandas

🌐 Simulação de API para obtenção de dados de usuários (mock)

📝 Geração de mensagens personalizadas

🔄 Mock de atualização de usuários com retorno de sucesso

🚀 Como usar
## Instale dependências
pip install pandas requests

## Execute o script
python main.py

Mensagens personalizadas aparecerão no console.

🔗 Referências

Documentação API OpenAI

Gerar API Key OpenAI

--------

import pandas as pd

df = pd.read_csv('userID.csv')

user_ids = df['UserID'].tolist()

print(user_ids)

import requests

import json

UserID_api_url = "https://exemplo.com"

def get_user(id):
    return {
        "id": id,
        "name": f"User {id}",
        "news": []
    }

users = [user for id in user_ids if (user := get_user(id)) is not None]


print(json.dumps(users, indent=2))

openai_api_key = 'testetesteteste'

import random

## USUÁRIOS REAIS (mock)

users = [

    {
    
        "id": 1,
        
        "name": "Giovana",
        
        "news": []
        
    }
    

    
    {
    
        "id": 2,
        
        "name": "Carlos",
        
        "news": []
        
    }
    
]




## FUNÇÃO DE GERAÇÃO DE MENSAGEM

def generate_ai_news(user):
    templates = [
    
        f"{user['name']}, investir cedo é o caminho mais seguro para tranquilidade financeira.",
        
        f"{user['name']}, pequenos investimentos hoje constroem grandes conquistas amanhã.",
        
        f"{user['name']}, investir com planejamento transforma sonhos em objetivos reais.",
        
        f"{user['name']}, consistência nos investimentos vale mais do que pressa."
        
    ]

    return random.choice(templates)
    
## PROCESSAMENTO

for user in users:

    news = generate_ai_news(user)
    

    user["news"].append({
    
        "description": news
        
    })
    

## RESULTADO


for user in users:

    print(f"\nUsuário: {user['name']}")
    
    for item in user["news"]:
    
        print("-", item["description"])
        

def update_user(user):

    print(f"Usuário {user['name']} atualizado com sucesso (mock).")
    
    return True
    

for user in users:

  success = update_user(user)
  
  print(f"User {user['name']} updated? {success}!")s
  
