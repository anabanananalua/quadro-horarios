# Cálculo do Número de Veículos Necessários

## Variáveis do Sistema

Seja:
- \( T_v \) = Tempo total de viagem (em minutos)
- \( T_d \) = Tempo de descanso (em minutos)
- \( I \) = Intervalo entre saídas (em minutos)
- \( H_i \) = Hora inicial do período (em formato 24h)
- \( H_f \) = Hora final do período (em formato 24h)
- \( M_i \) = Minuto inicial do período
- \( M_f \) = Minuto final do período

## Fórmulas Base

1. **Tempo Total de Ciclo por Veículo:**
   \[ T_c = T_v + T_d \]
   Onde \( T_c \) é o tempo total que um veículo leva para completar um ciclo e estar disponível novamente.

2. **Número de Saídas em um Período:**
   \[ N_s = \left\lceil\frac{(H_f - H_i) \times 60 + (M_f - M_i)}{I}\right\rceil \]
   Onde \( N_s \) é o número de saídas necessárias no período.

3. **Número de Veículos Necessários por Período:**
   \[ N_v = \left\lceil\frac{T_c}{I}\right\rceil \]
   Onde \( N_v \) é o número mínimo de veículos necessários para manter as saídas no intervalo especificado.

## Exemplo Prático

Considerando:
- Tempo de viagem (\( T_v \)) = 100 minutos
- Tempo de descanso (\( T_d \)) = 5 minutos
- Intervalo entre saídas (\( I \)) = 6 minutos
- Período: 06:00 às 06:59 (completo)

Calculamos:

1. Tempo total de ciclo:
   \[ T_c = 100 + 5 = 105 \text{ minutos} \]

2. Número de saídas no período:
   \[ N_s = \left\lceil\frac{(6 - 6) \times 60 + (59 - 0)}{6}\right\rceil = \left\lceil\frac{59}{6}\right\rceil = 10 \text{ saídas} \]

3. Número de veículos necessários:
   \[ N_v = \left\lceil\frac{105}{6}\right\rceil = 18 \text{ veículos} \]

## Fórmula Geral para Múltiplos Períodos

Para calcular o número total de veículos necessários em múltiplos períodos:

\[ N_{total} = \max_{i=1}^{n} \left\lceil\frac{T_c}{I_i}\right\rceil \]

Onde:
- \( n \) é o número de períodos ativos
- \( I_i \) é o intervalo do período i
- \( N_{total} \) é o número total de veículos necessários

## Observações Importantes

1. O sistema sempre arredonda para cima (função teto ⌈x⌉) para garantir que haja veículos suficientes.
2. O número total de veículos é determinado pelo período que exige mais veículos.
3. A reutilização de veículos é possível quando:
   \[ T_{disponível} \leq T_{próxima_saída} \]
   Onde \( T_{disponível} \) é o momento em que o veículo estará disponível após completar um ciclo.

## Otimização

O sistema otimiza a utilização dos veículos:
1. Sempre tenta reutilizar o veículo com menor número disponível
2. Só cria um novo veículo quando nenhum veículo existente está disponível
3. Considera o tempo de descanso entre viagens para garantir a segurança operacional 