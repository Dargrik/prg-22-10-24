Pokročilé programové konstrukce v C#
Úvod do objektově orientovaného programování (OOP)
Objektově orientované programování (OOP) je metoda organizace kódu, která se soustředí na objekty. Tyto objekty mohou mít vlastnosti (atributy) a schopnosti (metody). Hlavní principy OOP jsou:

Zapouzdření: Skrytí vnitřní implementace objektu a přístup k datům pouze přes veřejné metody.
Dědičnost: Umožňuje vytvořit nové třídy na základě existujících tříd.
Polymorfismus: Umožňuje používat objekty různých typů prostřednictvím stejného rozhraní.
Třídy a objekty
Třídy jsou jako plány nebo šablony, podle kterých se vytvářejí objekty. Objekty jsou konkrétní instance těchto tříd.

Příklad:
csharp
Zkopírovat kód
public class Auto
{
    public string Znacka { get; set; }
    public string Model { get; set; }
    public int RokVyroby { get; set; }

    // Konstruktor
    public Auto(string znacka, string model, int rokVyroby)
    {
        Znacka = znacka;
        Model = model;
        RokVyroby = rokVyroby;
    }

    // Metoda
    public void VypisInformace()
    {
        Console.WriteLine($"{Znacka} {Model} ({RokVyroby})");
    }
}
Úkol:
Vytvořte třídu Student s vlastnostmi Jmeno, Prijmeni a Vek. Poté vytvořte metodu, která vypíše tyto informace o studentovi.
Dědičnost
Dědičnost umožňuje vytvářet nové třídy, které dědí vlastnosti a metody z jiných tříd. To vám umožňuje znovu využít kód a přidat nové funkce.

Příklad:
csharp
Zkopírovat kód
public class SportovniAuto : Auto
{
    public int MaximalniRychlost { get; set; }

    public SportovniAuto(string znacka, string model, int rokVyroby, int maximalniRychlost)
        : base(znacka, model, rokVyroby)
    {
        MaximalniRychlost = maximalniRychlost;
    }

    public void VypisRychlost()
    {
        Console.WriteLine($"Maximální rychlost: {MaximalniRychlost} km/h");
    }
}
Úkol:
Vytvořte třídu Zamestnanec, která dědí z třídy Osoba (můžete přidat vlastnosti jako Jmeno a Vek). Třída Zamestnanec bude mít navíc vlastnost Plat a metodu, která vypíše všechny údaje o zaměstnanci.
Rozhraní (interfaces)
Rozhraní definují sadu metod, které třída musí implementovat. Na rozdíl od dědičnosti, kdy třída dědí konkrétní funkce, rozhraní definuje jen „smlouvu“, co musí být implementováno.

Příklad:
csharp
Zkopírovat kód
public interface IAuto
{
    void Start();
    void Stop();
}

public class OsobniAuto : IAuto
{
    public void Start()
    {
        Console.WriteLine("Auto startuje...");
    }

    public void Stop()
    {
        Console.WriteLine("Auto zastavuje...");
    }
}
Úkol:
Vytvořte rozhraní IZvire s metodami Zvuk() a Jidlo(). Poté vytvořte třídy Pes a Kocka, které implementují toto rozhraní. Každá třída by měla vypisovat, jaký zvuk zvíře vydává a co jí.
Kolekce (List, Dictionary)
Kolekce jsou struktury, které umožňují ukládat více prvků najednou. Dva nejčastěji používané typy jsou List a Dictionary.

List: Seznam prvků, které lze přidávat nebo odebírat.
Dictionary: Páry klíč-hodnota, kde každý klíč musí být jedinečný.
Příklad (List):
csharp
Zkopírovat kód
List<string> seznam = new List<string>();
seznam.Add("Jablko");
seznam.Add("Banán");

foreach (var item in seznam)
{
    Console.WriteLine(item);
}
Příklad (Dictionary):
csharp
Zkopírovat kód
Dictionary<int, string> zamestnanci = new Dictionary<int, string>();
zamestnanci.Add(1, "Jan Novák");
zamestnanci.Add(2, "Petr Svoboda");

Console.WriteLine(zamestnanci[1]);  // Výstup: Jan Novák
Úkol:
Vytvořte List, který bude obsahovat několik objektů třídy Student a vypište informace o všech studentech.
Vytvořte Dictionary, kde klíčem bude ID studenta a hodnotou jméno studenta. Umožněte uživateli zadat ID a vypište odpovídajícího studenta.
Polymorfismus a přetěžování metod
Polymorfismus umožňuje, aby se jedna metoda chovala různě v závislosti na použitých parametrech. Přetěžování metod znamená, že můžete vytvořit více verzí stejné metody, které se liší typem nebo počtem argumentů.

Příklad:
csharp
Zkopírovat kód
public class Matematika
{
    public int Secti(int a, int b)
    {
        return a + b;
    }

    public double Secti(double a, double b)
    {
        return a + b;
    }
}
Úkol:
Přetěžte metodu Secti tak, aby mohla sčítat jak celá čísla, tak desetinná čísla.
