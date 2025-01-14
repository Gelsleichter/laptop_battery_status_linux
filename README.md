### Measure Battery Capacity on a Linux Laptop Using the Terminal:

---

Linux provides detailed information about the battery in the `/sys/class/power_supply/` directory. You can check the current capacity and the design capacity of the battery.

### **Steps:**

1. Navigate to the battery directory:
```bash
cd /sys/class/power_supply/BAT0
```
(If your laptop has more than one battery, there might also be a BAT1 directory.)

2. Check the design capacity (original battery capacity):
```bash
cat energy_full_design
```
The returned value will be in microampere-hours (µAh).

3. Check the current battery capacity:
```bash
cat energy_full
```

4. Calculate the percentage of the current capacity relative to the design capacity:
```bash
echo "$(cat energy_full) * 100 / $(cat energy_full_design)" | bc
```

Example Output:
If energy_full_design is 57000000 (57 Wh) and energy_full is 45000000 (45 Wh), the battery capacity will be:
45000000 * 100 / 57000000 = 78%
This indicates that the battery is at 78% of its original capacity.


---


### Medir a capacidade da bateria em laptop Linux, com o terminal:

---

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
