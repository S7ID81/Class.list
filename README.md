Using System;
using System.Collections.Generic;

public class Product
{
    public string n;
    public string c;
    public double p;
    public DateTime d;

    public void getData()
    {
        Console.WriteLine(n + " " + c + " " + p + " " + d.ToShortDateString());
    }

    public bool isExp()
    {
        return d < DateTime.Now;
    }
}

class Program
{
    static void Main()
    {
        List<Product> l = new List<Product>();

        Console.WriteLine("Mehsul sayi:");
        int k = Convert.ToInt32(Console.ReadLine());

        Product p1 = null;

        for (int i = 0; i < k; i++)
        {
            Product o = new Product();

            Console.WriteLine("Ad:");
            o.n = Console.ReadLine();

            Console.WriteLine("Kateqoriya:");
            o.c = Console.ReadLine();

            Console.WriteLine("Qiymet:");
            o.p = Convert.ToDouble(Console.ReadLine());

            Console.WriteLine("Tarix (il-ay-gun):");
            o.d = Convert.ToDateTime(Console.ReadLine());

            l.Add(o);

            if (i == 0)
            {
                p1 = o;
            }
        }

        foreach (Product i in l)
        {
            i.getData();
        }

        bool b = l.Contains(p1);
        Console.WriteLine("p1 var: " + b);

        Console.WriteLine("Filtirleme ucun kateqoriya:");
        string f = Console.ReadLine();
        List<Product> fl = filter(l, f);

        foreach (Product i in fl)
        {
            i.getData();
        }

        for (int i = l.Count - 1; i >= 0; i--)
        {
            if (l[i].isExp())
            {
                l.RemoveAt(i);
            }
        }
    }

    static List<Product> filter(List<Product> x, string y)
    {
        List<Product> z = new List<Product>();
        foreach (Product i in x)
        {
            if (i.c == y)
            {
                z.Add(i);
            }
        }
        return z;
    }
}
