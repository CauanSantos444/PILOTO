# Boas-vindas com o nome
print("Bem-vindo a Livraria do Cauan Thiago")

# Lista vazia de livros e variável global de id
lista_livros = []
id_global = 0

# Função para cadastrar livro
def cadastrar_livro(lista):
    global id_global
    id_global += 1
    print('-' * 42)
    print("-" * 10 , "MENU CADASTRAR LIVRO" , "-" * 10)
    print(f"ID do livro: {id_global}")
    nome = input("Por favor, entre com o nome do livro: ")
    autor = input("Por favor, entre com o autor do livro: ")
    editora = input("Por favor, entre com a editora do livro: ")
    livro = {"id": id_global, "nome": nome, "autor": autor, "editora": editora}
    lista.append(livro)
    print("Livro cadastrado com sucesso!")

# Função para consultar livro
def consultar_livro(lista):
    while True:
        print('-' * 42)
        print("-" * 10 , "MENU CONSULTAR LIVRO" , "-" * 10)
        print("Escolha a opção desejada:")
        print("1 - Consultar Todos")
        print("2 - Consultar por Id")
        print("3 - Consultar por Autor")
        print("4 - Retornar ao menu")   
        opcao = input("Qual opção deseja? ")
        if opcao == "1":
            print("Consulta de Todos os Livros:")
            for livro in lista:
                print('-' * 42)
                print("ID:", livro["id"])
                print("Nome:", livro["nome"])
                print("Autor:", livro["autor"])
                print("Editora:", livro["editora"])
        elif opcao == "2":
            id_consulta = int(input("Digite o id do livro: "))
            for livro in lista:
                if livro["id"] == id_consulta:
                    print('-' * 42)
                    print("Livro encontrado:")
                    print("ID:", livro["id"])
                    print("Nome:", livro["nome"])
                    print("Autor:", livro["autor"])
                    print("Editora:", livro["editora"])
                    break
            else:
                print("Livro não encontrado!")
        elif opcao == "3":
            autor_consulta = input("Digite o nome do autor: ")
            print(f"Livros do autor {autor_consulta}:")
            for livro in lista:
                if livro["autor"] == autor_consulta:
                    print('-' * 42)
                    print("ID:", livro["id"])
                    print("Nome:", livro["nome"])
                    print("Autor:", livro["autor"])
                    print("Editora:", livro["editora"])
        elif opcao == "4":
            break
        else:
            print("Opção inválida!")

# Função para remover livro
def remover_livro(lista):
    id_remover = int(input("Digite o id do livro a ser removido: "))
    for livro in lista:
        if livro["id"] == id_remover:
            lista.remove(livro)
            print("Livro removido com sucesso!")
            break
    else:
        print("Id inválido!")

# Menu principal
while True:
    print('-' * 36)
    print("-" * 10 , "MENU PRINCIPAL" , "-" * 10)
    print("Escolha a opção desejada:")
    print("1 - Cadastrar Livro")
    print("2 - Consultar Livro(s)")
    print("3 - Remover Livro")
    print("4 - Sair")

    opcao_menu = input(">> ")
    if opcao_menu == "1":
        cadastrar_livro(lista_livros)
    elif opcao_menu == "2":
        consultar_livro(lista_livros)
    elif opcao_menu == "3":
        remover_livro(lista_livros)
    elif opcao_menu == "4":
        print("Encerrando o programa...")
        break
    else:
        print("Opção inválida!")
