## Strategy
## Histórico de Versão

<table>
  <thead>
    <tr>
      <th>Data</th>
      <th>Autor(es)</th>
      <th>Descrição</th>
      <th>Versão</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>13/10/2020</td>
      <td>
        Caio César Beleza(<a target="blank" href="https://github.com/Caiocbeleza">Caiocbeleza</a>)
      </td>
      <td>Adicionando introdução do padrão strategy </td>
      <td>0.1</td>
    </tr>
    <tr>
      <td>13/10/2020</td>
      <td>
        Caio César Beleza(<a target="blank" href="https://github.com/Caiocbeleza">Caiocbeleza</a>)
      </td>
      <td>Adicionando estrutura do padrão strategy </td>
      <td>0.2</td>
    </tr>
    <tr>
      <td>13/10/2020</td>
      <td>
        Caio César Beleza(<a target="blank" href="https://github.com/Caiocbeleza">Caiocbeleza</a>)
      </td>
      <td>Adicionando trecho de código do projeto com padrão strategy </td>
      <td>0.3</td>
    </tr>
  </tbody>
</table>

## Introdução

<p align="justify">&emsp;
O Strategy é um padrão comportamental que permite definir uma família de algorítmos, colocá-los em classes separadas e fazer com que seus objetos sejam permutáveis.
</p>
<p align="justify">&emsp;
Este padrão sugere que você pegue uma classe que faz algo específico em diversas maneiras diferentes e extraia todos esses algoritmos para classes separadas chamadas strategy.
</p>

## Estrutura
![Estrutura Strategy](../../images/design_patterns/strategyStructure.png)

<p align="justify">&emsp;
- "Context" mantém uma referência para uma "ConcreteStrategy" e se comunica com esse objeto através da interface "Strategy".
</p>
<p align="justify">&emsp;
- A interface "Strategy" é comum à todas "ConcreteStrategy". Ela declara um método uqe o "Context" usa para executar uma "Strategy"
</p>
<p align="justify">&emsp;
- As "ConcreteStrategy" implementam diferentes variações de um algoritmo que o "Context" usa.
</p>
<p align="justify">&emsp;
- O "Context" chama o método de execução no objeto "Strategy" ligado cada vez que ele precisa rodar um algorítmo. O "Context" não sabe qual tipo de "Strategy" ele está trabalhando ou como o algoritmo é executado.
</p>
<p align="justify">&emsp;
- O "Client" cria um objeto "Strategy" específico e passa ele para "Context". O "Context" expõe um setter que permite o "Client" mudar o "Strategy" associada com o "Context" durante a execução.
</p>


## Aplicações no Projeto(QRodízio)

```
def permission_strategy_factory(role):
    """Given a role, returns a permission strategy for that role"""
    if role == EmployeeRole.basic:
        return basic_permission_strategy
    elif role == EmployeeRole.manager:
        return manager_permission_strategy
    else:
        return no_permission_strategy


def no_permission_strategy(*args, **kwargs):
    """No permission at all"""
    return False


def manager_permission_strategy(employee):
    """Manager permission user must be a manager"""
    if employee.role == EmployeeRole.manager:
        return True

    return False


def basic_permission_strategy(employee):
    """Baasic permission user just need to be logged"""
    return True


```


## Referências
<ul>
<li>
REFACTORING.GURU. Strategy. Disponível em: https://refactoring.guru/pt-br/design-patterns/strategy . Acesso em: 13 de outubro. 2020.
</li>
<li>
SOURCEMAKING. Design Patters. https://sourcemaking.com/design_patterns . Acesso em: 13 de outubro. 2020.
</li>
</ul>