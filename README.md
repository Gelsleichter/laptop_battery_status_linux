Medir a capacidade da bateria em laptop Linux, com o terminal:

---

## **1. Usando Arquivos do Sistema (`/sys/class/power_supply`)**

O Linux fornece informações detalhadas sobre a bateria no diretório `/sys/class/power_supply/`. Você pode verificar a capacidade atual e a capacidade de projeto (design capacity) da bateria.

### **Passos:**

1. Navegue até o diretório da bateria:
```bash
   cd /sys/class/power_supply/BAT0
```
(Se o seu laptop tiver mais de uma bateria, pode haver um diretório BAT1 também.)

2. Verifique a capacidade de projeto (capacidade original da bateria):
```bash
cat energy_full_design
```   
O valor retornado será em microampere-horas (µAh).

3. Verifique a capacidade atual da bateria:
```bash
cat energy_full
``` 

4. Calcule a porcentagem da capacidade atual em relação à capacidade de projeto:
```bash
echo "$(cat energy_full) * 100 / $(cat energy_full_design)" | bc
```

Exemplo de Saída:
Se energy_full_design for 57000000 (57 Wh) e energy_full for 45000000 (45 Wh), a capacidade da bateria será:
45000000 * 100 / 57000000 = 78%

Isso indica que a bateria está com 78% da capacidade original.
