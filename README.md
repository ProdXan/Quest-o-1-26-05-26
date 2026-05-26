# Quest-o-1-26-05-26
Atividade Estrutura de Dados

Conceitos Básicos
1. O que é uma pilha em programação?
Pensa numa pilha de pratos na pia da sua cozinha. Quando você vai lavar, você pega o prato que está lá no topo, certo? E se chega um prato novo para lavar, você coloca ele onde? No topo também. Em programação, uma pilha é exatamente isso: uma estrutura de dados onde você só mexe na extremidade superior (o topo). Você insere elementos ali e remove dali.

2. A principal regra e o conceito de LIFO
A regra de ouro é: o último que entra é o primeiro que sai.
Daí vem a sigla LIFO (Last In, First Out). Se você colocar os números 1, 2 e 3 nessa ordem dentro de uma pilha, o 3 ficou no topo. Portanto, se precisar tirar alguém, obrigatoriamente vai ser o 3.

Mão na Massa com Python (Exercícios 3 ao 11)
Em Python, a forma mais nativa e comum de simular uma pilha é usando uma lista comum. O método .append() coloca elementos no topo (fim da lista) e o .pop() remove do topo.

3. Criar uma pilha vazia
Python
pilha = []
4. Adicionar 5 elementos usando append()
Python
pilha.append("A")
pilha.append("B")
pilha.append("C")
pilha.append("D")
pilha.append("E")
5. Remover o último elemento usando pop() e exibir
Python
removido = pilha.pop()
print("Elemento removido:", removido)
6. Adicionar 10, 20, 30, 40 e exibir a pilha completa
Python
numeros = []
numeros.append(10)
numeros.append(20)
numeros.append(30)
numeros.append(40)

print("Pilha completa:", numeros)
7. Remover todos os elementos, um por um, exibindo cada um
Python
minha_pilha =

while len(minha_pilha) > 0:
    removido = minha_pilha.pop()
    print(f"Removido: {removido}")
8. Verificar se a pilha está vazia antes de remover
Python
teste_pilha = []

if not teste_pilha:  # Em Python, listas vazias são avaliadas como False
    print("A pilha está vazia! Não dá para remover nada.")
else:
    teste_pilha.pop()
9. Pilha de livros e mostrar quem está no topo
Python
livros = ["O Senhor dos Anéis", "1984", "O Hobbit", "Dom Casmurro"]

# O topo é sempre o último índice da lista (-1)
if livros:
    print("Livro no topo:", livros[-1])
10 e 11. Ler 5 nomes, armazenar e exibir na ordem inversa
Python
nomes = []

# Lendo os 5 nomes
for i in range(5):
    nome = input(f"Digite o {i+1}º nome: ")
    nomes.append(nome)

print("\nRetirando da pilha (ordem inversa):")
# Removendo e mostrando (o comportamento natural da pilha inverte a ordem)
while nomes:
    print(nomes.pop())
Criando Funções Próprias (Exercícios 12 ao 15)
Para deixar o código mais organizado, podemos encapsular o comportamento da pilha em funções.

Python
# 12. Função para empilhar
def empilhar(pilha, valor):
    pilha.append(valor)

# 13. Função para desempilhar
def desempilhar(pilha):
    if not esta_vazia(pilha):
        return pilha.pop()
    return "Pilha já está vazia!"

# 14. Função para olhar o topo sem remover
def topo(pilha):
    if not esta_vazia(pilha):
        return pilha[-1]
    return "Pilha vazia"

# 15. Função para verificar se está vazia
def esta_vazia(pilha):
    return len(pilha) == 0
Aplicações Práticas e Menus (Exercícios 16 ao 20)
16 e 17. Simulação de Pilha de Pratos com Menu Interativo
Aqui juntamos a lógica de pratos com o sistema de menu para o usuário interagir.

Python
pilha_pratos = []

while True:
    print("\n--- MENU DA PILHA ---")
    print("1. Empilhar (Adicionar prato)")
    print("2. Desempilhar (Lavar prato do topo)")
    print("3. Mostrar topo")
    print("4. Mostrar pilha completa")
    print("5. Sair")
    
    opcao = input("Escolha uma opção: ")
    
    if opcao == "1":
        cor_prato = input("Digite a cor ou tipo do prato: ")
        pilha_pratos.append(cor_prato)
        print(f"Prato '{cor_prato}' adicionado ao topo.")
        
    elif opcao == "2":
        if pilha_pratos:
            lavado = pilha_pratos.pop()
            print(f"Prato '{lavado}' foi removido para ser lavado.")
        else:
            print("Nenhum prato na pilha!")
            
    elif opcao == "3":
        if pilha_pratos:
            print(f"Prato no topo atual: {pilha_pratos[-1]}")
        else:
            print("Pilha vazia.")
            
    elif opcao == "4":
        print("Pilha atual (da base ao topo):", pilha_pratos)
        
    elif opcao == "5":
        print("Saindo do programa...")
        break
    else:
        print("Opção inválida, tente de novo.")
18. Inverter uma palavra usando pilha
Python
palavra = input("Digite uma palavra para inverter: ")
pilha_letras = []

# Empilha letra por letra
for letra in palavra:
    pilha_letras.append(letra)

palavra_invertida = ""
# Desempilha construindo a nova string
while pilha_letras:
    palavra_invertida += pilha_letras.pop()

print("Palavra invertida:", palavra_invertida)
19. Verificar se é um Palíndromo (ex: "arara", "radar")
Python
texto = input("Digite uma palavra/frase para testar se é palíndromo: ").lower().replace(" ", "")
pilha_caracteres = []

for char in texto:
    pilha_caracteres.append(char)

texto_invertido = ""
while pilha_caracteres:
    texto_invertido += pilha_caracteres.pop()

if texto == texto_invertido:
    print("É um palíndromo!")
else:
    print("Não é um palíndromo.")
20. Caso do Mundo Real: O botão "Desfazer" (Ctrl + Z)
No mundo real, o uso mais famoso de pilhas em softwares é o histórico de ações (o famoso "Undo" ou Ctrl + Z). Cada alteração que você faz em um editor de texto vai para uma pilha. Quando você desfaz, ele tira a última alteração do topo.

Aqui está um exemplo simples simulando o histórico de um editor de textos:

Python
historico_editor = []

# Usuário digitando no editor
historico_editor.append("Digitei: 'Olá Mundo'")
historico_editor.append("Digitei: 'Estou aprendendo Python'")
historico_editor.append("Deletei o parágrafo 2 por engano")

print("Ações realizadas:", historico_editor)

# Ops, fiz besteira, vou dar Ctrl+Z
print("\n[Pressionou Ctrl + Z]")
ultima_acao = historico_editor.pop()
print(f"Ação desfeita: '{ultima_acao}'")

print("\nEstado atual do histórico:", historico_editor)
