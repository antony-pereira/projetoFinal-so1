# Simulador de rede de entregas
## Autores: Antony Muller Pereira e Otávio Scarparo Souza
## Como usar
`python3 main.py [S] [C] [P] [A]`
## Explicação
Esse projeto é uma simulação de um sistema logístico para gerenciamento de encomendas, veículos e pontos de redistribuição, desenvolvido em Python utilizando conceitos de multithreading. O sistema cria encomendas com pontos de origem e destino aleatórios, que são transportadas por veículos entre os pontos. Cada encomenda gera um arquivo de rastro contendo informações detalhadas sobre o transporte, incluindo horários e identificadores do veículo. Além disso, há um monitoramento em tempo real do status das encomendas e veículos, permitindo visualizar o progresso e a entrega das encomendas. O código utiliza filas, locks e semáforos para gerenciar a sincronização entre threads e garantir o correto funcionamento do sistema.
## Detalhes da implementação
Há três funções principais, uma para encomendas, uma para veículos e outra para pontos.
### Encomendas
São gerados aleatoriamente um ponto de início e um de destino. Enquanto ela não for entregue a thread dorme.
### Veículos
É gerado aleatoriamente um ponto de início. Enquanto houverem encomendas não entregues globalmente ele recolhe as que estiverem em um determinado ponto e as entrega. Recolher encomendas é uma seção crítica, então é usada uma lock para prevenir que tenha mais de um veículo recolhendo no mesmo ponto. Os veículos viajam entre pontos que são organizados em uma fila circular, o tempo de viagem é aleatório, um veículo pode chegar primeiro ao proximo ponto mesmo saindo antes.
### Pontos
A função monitora e avisa quando todas as encomendas dele forem retiradas.
