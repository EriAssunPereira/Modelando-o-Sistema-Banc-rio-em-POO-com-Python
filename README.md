# Modelando-o-Sistema-Banc-rio-em-POO-com-Python
Como atualizar a implementação do sistema bancário para usar objetos em vez de dicionários. Aqui está um exemplo de como podemos modelar as classes para representar clientes e contas bancárias:

```python
class Cliente:
    def __init__(self, nome, cpf):
        self.nome = nome
        self.cpf = cpf

class ContaBancaria:
    def __init__(self, numero, cliente):
        self.numero = numero
        self.cliente = cliente
        self.saldo = 0.0

    def depositar(self, valor):
        self.saldo += valor

    def sacar(self, valor):
        if self.saldo >= valor:
            self.saldo -= valor
        else:
            print("Saldo insuficiente.")

# Exemplo de uso:
cliente1 = Cliente("João", "123.456.789-00")
conta1 = ContaBancaria("12345", cliente1)

conta1.depositar(1000.0)
print(f"Saldo da conta {conta1.numero}: R${conta1.saldo:.2f}")

conta1.sacar(500.0)
print(f"Saldo da conta {conta1.numero}: R${conta1.saldo:.2f}")
```

Neste exemplo, temos duas classes: `Cliente` e `ContaBancaria`. A classe `Cliente` armazena informações sobre o nome e CPF do cliente. A classe `ContaBancaria` representa uma conta bancária com um número, um cliente associado e um saldo. As operações de depósito e saque são implementadas como métodos da classe `ContaBancaria`.

Nós podemos adaptar esse modelo de classes para atender às necessidades específicas do seu sistema bancário. 

Como criar uma classe para representar transações bancárias. Vou adicionar uma classe chamada `TransacaoBancaria` que pode ser usada para registrar depósitos e saques em uma conta bancária. Aqui está um exemplo:

```python
class TransacaoBancaria:
    def __init__(self, tipo, valor):
        self.tipo = tipo  # Pode ser "Depósito" ou "Saque"
        self.valor = valor

class ContaBancaria:
    def __init__(self, numero, cliente):
        self.numero = numero
        self.cliente = cliente
        self.saldo = 0.0
        self.transacoes = []  # Lista para armazenar as transações

    def depositar(self, valor):
        self.saldo += valor
        self.transacoes.append(TransacaoBancaria("Depósito", valor))

    def sacar(self, valor):
        if self.saldo >= valor:
            self.saldo -= valor
            self.transacoes.append(TransacaoBancaria("Saque", valor))
        else:
            print("Saldo insuficiente.")

    def listar_transacoes(self):
        for t in self.transacoes:
            print(f"{t.tipo}: R${t.valor:.2f}")

# Exemplo de uso:
cliente1 = Cliente("João", "123.456.789-00")
conta1 = ContaBancaria("12345", cliente1)

conta1.depositar(1000.0)
conta1.sacar(500.0)

print(f"Saldo da conta {conta1.numero}: R${conta1.saldo:.2f}")
print("Transações:")
conta1.listar_transacoes()
```

Neste exemplo, a classe `TransacaoBancaria` registra o tipo de transação (depósito ou saque) e o valor da transação. A classe `ContaBancaria` agora mantém uma lista de transações associadas à conta. O método `listar_transacoes` exibe todas as transações realizadas na conta.

Podemos adaptar essa estrutura conforme necessário para atender aos requisitos específicos do sistema bancário.

https://github.com/digitalinnovationone/trilha-python-dio/blob/main/01%20-%20Estrutura%20de%20dados/desafio.py
