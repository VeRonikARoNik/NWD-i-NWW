wykonanezadania100@gmail.com
# 🔢 NWD i NWW — aplikacja .NET WinForms

Ten projekt przedstawia prostą aplikację Windows Forms, która oblicza:

- **NWD – Największy Wspólny Dzielnik**
- **NWW – Najmniejszą Wspólną Wielokrotność**

Użytkownik wpisuje dwie liczby, zaznacza odpowiedni checkbox, a program wyświetla wynik.

---

# 📘 Teoria (proste wyjaśnienie)

## 🟦 NWD — Największy Wspólny Dzielnik
NWD to **największa liczba**, która dzieli dwie liczby **bez reszty**.

Przykład:  
NWD(12, 18) = 6  
Dzielniki:  
- 12 → 1,2,3,4,6,12  
- 18 → 1,2,3,6,9,18  
Największy wspólny to **6**.

### ✔ Algorytm Euklidesa (najprostszy sposób)
1. Dzielimy większą liczbę przez mniejszą.  
2. Bierzemy *resztę*.  
3. Zamieniamy liczby miejscami.  
4. Powtarzamy aż reszta = 0.  
5. Ostatnia niezerowa liczba → **NWD**.

Przykład:
48 mod 18 = 12
18 mod 12 = 6
12 mod 6 = 0
NWD = 6


---

## 🟩 NWW — Najmniejsza Wspólna Wielokrotność
NWW to najmniejsza liczba, która jest **wielokrotnością obu liczb**.

Przykład:  
NWW(4, 6) = 12

Bo:  
- wielokrotności 4 → 4,8,12,16…  
- wielokrotności 6 → 6,12,18…  
Pierwszy wspólny → **12**.

### ✔ Najważniejszy wzór:

NWW(a, b) = (a * b) / NWD(a, b)

<img width="516" height="259" alt="image" src="https://github.com/user-attachments/assets/b695639d-41e2-4800-ac99-089dce4b381f" />



```
# NWD-i-NWW
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace NWDiNWW
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            // Sprawdzenie danych wejściowych
            if (!int.TryParse(textBox1.Text, out int a) ||
                !int.TryParse(textBox2.Text, out int b))
            {
                MessageBox.Show("Wprowadź poprawne liczby całkowite!");
                return;
            }

            if (!checkBox1.Checked && !checkBox2.Checked)
            {
                MessageBox.Show("Zaznacz NWD lub NWW.");
                return;
            }

            string wynik = "";

            // NWD
            if (checkBox1.Checked)
            {
                int nwd = NWD(a, b);
                wynik += "NWD = " + nwd + "\n";
            }

            // NWW
            if (checkBox2.Checked)
            {
                int nwd = NWD(a, b);
                long nww = Math.Abs((long)a * b) / nwd;
                wynik += "NWW = " + nww;
            }

            MessageBox.Show(wynik);
        }

        // ⬇️⬇️⬇️ Funkcja NWD — musi być tutaj, w klasie, ale poza button1_Click
        private int NWD(int a, int b)
        {
            a = Math.Abs(a);
            b = Math.Abs(b);

            while (b != 0)
            {
                int temp = b;
                b = a % b;
                a = temp;
            }
            return a;
        }
    }
}
```
https://www.plukasiewicz.net/CSharp_dla_poczatkujacych/Struktury


### Pomocne linki do nauki:
### https://blog.przemyslawsobolewski.com/nww-i-nwd-w-c/
### https://rrogacz.pl/c-nwdnww
