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
