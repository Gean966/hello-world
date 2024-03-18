import random

def jogo_adivinhacao():
    print("Bem-vindo ao Jogo de Adivinhação!")
    print("Estou pensando em um número entre 1 e 100...")
    numero_secreto = random.randint(1, 100)
    tentativas = 0
    
    while True:
        chute = int(input("Digite o seu palpite: "))
        tentativas += 1
        
        if chute < numero_secreto:
            print("Tente um número maior!")
        elif chute > numero_secreto:
            print("Tente um número menor!")
        else:
            print(f"Parabéns! Você acertou o número em {tentativas} tentativas!")
            break

# Chame a função para iniciar o jogo
jogo_adivinhacao()
