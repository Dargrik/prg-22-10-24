# Pokročilé programové konstrukce v C#

## Úvod do objektově orientovaného programování (OOP)

Objektově orientované programování (OOP) je metoda organizace kódu, která se soustředí na **objekty**. Tyto objekty mohou mít vlastnosti (atributy) a schopnosti (metody). Hlavní principy OOP jsou:

- **Zapouzdření**: Skrytí vnitřní implementace objektu a přístup k datům pouze přes veřejné metody.
- **Dědičnost**: Umožňuje vytvořit nové třídy na základě existujících tříd.
- **Polymorfismus**: Umožňuje používat objekty různých typů prostřednictvím stejného rozhraní.

### Třídy a objekty

Třídy jsou jako plány nebo šablony, podle kterých se vytvářejí objekty. Objekty jsou konkrétní instance těchto tříd.

#### Příklad:

```csharp
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

V uvedeném kódu vidíme jednoduchou **třídu** Auto, která reprezentuje nějaké auto. Třída obsahuje tři **atributy** (vlastnosti): Znacka, Model a RokVyroby. Tyto vlastnosti jsou veřejné, což znamená, že jsou dostupné odkudkoliv v programu, a jsou definovány pomocí tzv. **getterů** a **setterů**.

Kromě toho třída obsahuje **konstruktor** a jednu **metodu**.

- **Konstrukto**r: Tento konstruktor nám umožňuje vytvářet instance třídy Auto a ihned nastavit jejich vlastnosti.
- **Metoda VypisInformace()**: Vypisuje informace o autě (značka, model a rok výroby) do konzole.

Příklad použití:
Auto auto1 = new Auto("Škoda", "Octavia", 2015);
auto1.VypisInformace(); // Výstup: Škoda Octavia (2015)

**Gettery a settery**

Getter je metoda, která umožňuje získat hodnotu nějaké vlastnosti. **Setter** je metoda, která umožňuje nastavit hodnotu nějaké vlastnosti. V C# se používá zkrácená syntaxe pro gettery a settery - automatické vlastnosti.

Příklad getteru a setteru s validací:
private int rokVyroby;
public int RokVyroby
{
    get { return rokVyroby; }
    set
    {
        if (value > DateTime.Now.Year)
        {
            throw new ArgumentException("Rok výroby nemůže být v budoucnosti.");
        }
        rokVyroby = value;
    }
}

Tři základní principy OOP

1. **Zapouzdření** (Encapsulation)

Zapouzdření znamená, že objekt skryje svou vnitřní implementaci a poskytuje přístup k datům pouze prostřednictvím veřejných metod.

Příklad v C#:
public class BankovniUcet
{
    private decimal zustatek;

    public decimal Zustatek
    {
        get { return zustatek; }
    }

    public void VlozPenize(decimal castka)
    {
        if (castka > 0)
        {
            zustatek += castka;
        }
    }

    public void VyberPenize(decimal castka)
    {
        if (castka > 0 && castka <= zustatek)
        {
            zustatek -= castka;
        }
    }
}

2. **Dědičnost** (Inheritance)

Dědičnost umožňuje vytvářet nové třídy, které dědí vlastnosti a metody z jiné třídy.

Příklad v C#:
public class DopravniProstredek
{
    public int MaximalniRychlost { get; set; }

    public void Pohyb()
    {
        Console.WriteLine("Dopravní prostředek se pohybuje.");
    }
}

public class Auto : DopravniProstredek
{
    public string Znacka { get; set; }

    public void Trub()
    {
        Console.WriteLine("Auto troubí!");
    }
}

3. **Polymorfismus**

Polymorfismus znamená, že můžeme použít objekty různých tříd prostřednictvím stejného rozhraní nebo metody.

Příklad v C#:
public class Zvire
{
    public virtual void VydatZvuk()
    {
        Console.WriteLine("Zvire vydává zvuk.");
    }
}

public class Pes : Zvire
{
    public override void VydatZvuk()
    {
        Console.WriteLine("Pes štěká.");
    }
}

public class Kocka : Zvire
{
    public override void VydatZvuk()
    {
        Console.WriteLine("Kočka mňouká.");
    }
}

Polymorfismus v akci:
Zvire mojeZvire = new Pes();
mojeZvire.VydatZvuk();  // Výstup: Pes štěká.

mojeZvire = new Kocka();
mojeZvire.VydatZvuk();  // Výstup: Kočka mňouká.
