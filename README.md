sing System.Runtime.InteropServices;

namespace DomacneUkol45
{
    internal class Program
    {
        static void Main(string[] args)
        {

            Pohori pohori1 = new Pohori("Bumb");

            pohori1.AddHora(new Hora("asd", 984));
            pohori1.AddHora(new Hora("asdasd hora", 4984));
            pohori1.AddHora(new Hora("asdasda hora", 1555));

            HashSet<Hora> nejHory = pohori1.NejvyssiHora();
            Console.WriteLine("V pohori "+ pohori1.JmenoPohori + " jsou "+ pohori1.PocetHor()+" hory");
            foreach (Hora h in nejHory) 
            {
                Console.WriteLine(h.ToString());
            }

            















            Student karel = new Student("Karel", "IV", 1.5);
            Student pepa = new Student("Pepa", "Dědek", 1.5);
            Student marek = new Student("Marek", "Václav", 3.2);
            Student jarda = new Student("Jaroslav", "Bílek", 5);
            Trida trida = new Trida("4A", "Novotná");
            trida.addStudent(karel);
            trida.addStudent(pepa);
            trida.addStudent(marek);
            trida.addStudent(jarda);
            Console.WriteLine("Trida" +trida.JmenoTridy+ "má"+ trida.Pocet()+" studentů.");
            Console.WriteLine("Průměr známek ve třídě"+ trida.JmenoTridy+ "je" +trida.celkPrumer()+".");

            List<Student> nejlepsiStudenti = trida.BestStudent();

            if (nejlepsiStudenti.Count > 0)
            {
                foreach (var student in nejlepsiStudenti)
                {
                    Console.WriteLine("Nejlepší student je "+student.Jmeno+" "+ student.Prijmeni+" a má průměr "+ student.Prumer);

                }
            }
            else
            {
                Console.WriteLine("Ve třídě nejsou žádní studenti.");

            }
        }
    }
}



using System;
using System.Collections.Generic;
using System.Data;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DomacneUkol45
{
    internal class Pohori
    {
        private string jmenoPohori;
        private HashSet<Hora> hory = new HashSet<Hora>();

        public string JmenoPohori { get => jmenoPohori; set => jmenoPohori = value; }

        public Pohori(string jmenoPohori) {
            JmenoPohori= jmenoPohori;
        }

        public bool AddHora(Hora hora) 
        {
            return hory.Add(hora);
        }
      
        public int PocetHor() 
        {
            return hory.Count;
        }

        public HashSet<Hora> NejvyssiHora() 
        {
            HashSet<Hora> nejvyissiHory = new();
            Hora horaNej = hory.First();
            foreach (Hora h in hory) 
            {
                if (h.Vyska == horaNej.Vyska)
                {
                    nejvyissiHory.Add(h);
                }
            }
            return nejvyissiHory;
        }



    }
}





using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DomacneUkol45
{
    internal class Hora
    {
        private string jmeno;
        private int vyska;

        public string Jmeno { get => jmeno; set => jmeno = value; }
        public int Vyska { get => vyska; set => vyska = value; }

        public Hora(string jmeno, int vyska) 
        {
            this.jmeno = jmeno;
            this.vyska = vyska;
        }
        

        public override string ToString()
        {
            return jmeno + " " + vyska;
        }

        public override bool Equals(object? obj)
        {
            return obj is Hora hora &&
                jmeno == hora.jmeno;
        }
        public override int GetHashCode()
        {
            return base.GetHashCode();
        }
    }
}







