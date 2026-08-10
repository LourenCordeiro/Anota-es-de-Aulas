# Herança em Python
## Continuação das aulas de Python orientadas a objeto(OOP)

Existem 4 pilares no conceito Programação Orientada a Objeto:  

1-Abstração  

2-Encapsulamento  

3-Herança  

4-Polimorfismo  

## **HERANÇA (Generalização)**
 É um relacionamento(**do tipo é UM**) entre itens gerais (ancestral/classe base/classe mãe) e tipos mais específicos (descendente/classe derivada/classe filha) desses itens, que herdam atributos e métodos dos níveis superiores. (de forma simples, os itens descendentes ou derivados vão "herdar" atributos e métodos dos itens ancestrais ou superiores, mas também pode criar atributos e métodos novos).Nos diagramas a herança é representada como uma seta para cima.

## Principais Vantagens  

- Reutilização de códigos (classes superiores podem ser utilizadas em outros códigos
- Organização hierárquica
- Facilidade de manutenção
- Extensibilidade (uma alteração em classe superior vai beneficiar as que estiverem inferiores)
- Suporte a polimorfismo

## Na imagem trás um exemplo prático de como seria uma organização de herança, com a parte de cima sendo generalizada e as de baixo sendo especializadas

<img width="1498" height="916" alt="image" src="https://github.com/user-attachments/assets/b47228a4-0939-4588-88c6-049ffe83dac2" />

Tradução da imagem para a linguagem Python:
```
from rich import print, inspect

class Pessoa:
    def __init__(self, nome="", idade=0):
        self.nome = nome
        self.idade = idade

    def fazer_aniversario(self):
        self.idade += 1


class Aluno(Pessoa):                    #aqui a classe "Pessoa" entre parênteses liga os atributos da classe mãe
    def __init__(self, nome, idade, curso, turma):
        super().__init__(nome, idade)           #comando para trazer os atributos solicidades da classe mãe
        self.curso = curso
        self.turma = turma

    def fazer_matricula(self):
        print(f"{self.nome} acabou de fazer matrícula")


class Professor(Pessoa):
    def __init__(self, nome, idade, especialidade, nivel):
        super().__init__(nome, idade)
        self.especialidade = especialidade
        self.nivel = nivel

    def dar_aula(self):
        print(f"Prof. {self.nome} começou a dar aula")


class Funcionario(Pessoa):
    def __init__(self, nome, idade, cargo, setor):
        super().__init__(nome, idade)
        self.cargo = cargo
        self.setor = setor

    def bater_ponto(self):
        print(f"{self.nome} acabou de bater ponto.")


a1 = Aluno("José", 17, "Informática", "T01")
a1.fazer_aniversario()
a1.fazer_matricula()
inspect(a1, methods=True)

p1 = Professor("Samuel", 37, "Biologa", "Mestrado")
p1.fazer_aniversario()
p1.dar_aula()
#inspect(p1, methods=True)

f1 = Funcionario("CLáudia", 27, "Secretária", "Secretaria")
f1.fazer_aniversario()
f1.bater_ponto()
#inspect(f1, methods=True)
```
*Esse exemplo foi usado como exercício (004)*

## **ABSTRAÇÃO**  

A prática de ignorar o irrelevante e se focar estritamente no essencial. Existe abstração de dados, que acontece quando ignoramos informações desnecessárias para o escopo do projeto. Existe abstração de processos, quando não precisamos saber como um método faz seu trabalho, apenas sabe que ele existe pela interface.

## Principais Vantagens  

- Maior legibilidade (é mais fácil entender um código que está mais objetivo)
- Padronização 
- Simplificação
- Segurança

> Classe Abstrata: funciona como uma base para as subclasses se transformarem em objetos.(não serve para gerar objetos)
> Método Abstrato: estão dentro de classes abstratas, obriga a subclasse a ter um método. (não possuem linhas de programação)

DRY - Don't Repeat Yourself
