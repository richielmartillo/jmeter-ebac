# Teste de Performance com JMeter - BlazeDemo

Este repositório contém um teste de performance desenvolvido com Apache JMeter, utilizando como base o site BlazeDemo.

O objetivo do projeto é simular múltiplos usuários acessando um fluxo de navegação, utilizando massa de dados parametrizada por arquivo CSV.

## Ferramentas utilizadas

- Apache JMeter 5.6.3
- CSV Data Set Config
- BlazeDemo
- Git e GitHub
- BlazeMeter para validação complementar em nuvem

## Arquivos do projeto

- `BLAZEDEMO-TEST.jmx`: plano de teste criado no JMeter.
- `termos.csv`: arquivo CSV utilizado como massa de dados para parametrizar origem e destino das viagens.

## Configuração do teste

O teste foi configurado com os seguintes parâmetros:

- 50 usuários virtuais
- Ramp-up de 3 minutos
- Tempo de execução de 5 minutos
- Massa de dados via CSV
- Execução do fluxo no site BlazeDemo

## Fluxo testado

O plano de teste simula o seguinte fluxo no BlazeDemo:

1. Acesso à reserva de voo
2. Seleção de origem e destino utilizando dados do CSV
3. Compra/passagem
4. Confirmação da operação

## Massa de dados

O arquivo `termos.csv` contém combinações de cidades utilizadas nos parâmetros:

- `fromPort`
- `toPort`

Essas variáveis são utilizadas no JMeter da seguinte forma:

```text
${fromPort}
${toPort}

Resultados

O teste foi executado localmente no Apache JMeter e finalizou com sucesso no Summary Report, apresentando:

0.00% de erros
1302 samples
Tempo médio de resposta aproximado de 757 ms
Throughput aproximado de 4.3 requisições por segundo

Também foi realizada uma validação complementar no BlazeMeter.
Durante a execução em nuvem, algumas requisições para confirmation.php retornaram "Too Many Requests", indicando limitação do ambiente externo do site testado.
