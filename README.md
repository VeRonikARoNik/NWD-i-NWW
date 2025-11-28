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
