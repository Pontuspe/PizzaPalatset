# PizzaPalatset
namespace CustomerTerminal
{
    public static class Lists
    {

        // Lista som visar maträttsmenyn
        public static List<string> FoodMenu = new List<string>
        {
            "Välj den typ av mat som du vill beställa:",
            "-------------\n",
            "1. Pizza",
            "2. Pasta",
            "3. Sallad",
            "4. Dryck",
            "5. Visa pågående order\n",

            "-------------",
            "6. Avsluta"
        };

        //Lista som visar de olika valen som går att göra när användaren kontrollerar sin pågående order
        public static List<string> CurrentOrderMenu = new List<string>
        {
            "1. Bekräfta och gå till betalning",
            "2. Fortsätt handla",
            "3. Ta bort innehåll\n",

            "-------------",
            "4. Avsluta"
        };

        //Lista som visar de produkter som användaren beställt
        public static List<string> CurrentOrder = new List<string>();


        //Lista som visar Pizzorna på restaurangen
        public static List<string> Pizzas = new List<string>
        {
            "Pizzameny",
            "-------------\n",

            "1. Vesuvio (skinka, ost, tomatsås)\t\t80:-",
            "2. Margarita (ost, tomatsås)\t\t\t80:-",
            "3. Hawaii (skinka, ost, ananas, tomatsås)\t80:-",
            "4. Calzone (skinka, ost, tomatsås, inbakad)\t80:-\n",

            "-------------",
            "5. Återgå",
            "6. Avsluta"

        };

        //Lista som visar de olika bottnarna som finns att välja på
        public static List<string> PizzaBottoms = new List<string>
        {
            "Välj vilken botten du vill ha på pizzan",
            "-------------\n",

            "1. Italiensk",
            "2. Amerikansk\n",

            "------------",
            "3. Återgå",
            "4. Avsluta"
        };


        //Lista över de olika salladerna på restaurangen
        public static List<string> Salads = new List<string>
        {
            "Salladsmeny",
            "-------------\n",

            "1. Mozarellasallad\t80:-",
            "2. Chevresallad\t\t80:-\n",

            "-------------",
            "3. Fortsätt handla",
            "4. Avsluta"
        };

        //Lista över de olika pastasorterna på restaurangen
        public static List<string> Pastas = new List<string>
        {
            "Pastameny",
            "-------------\n",

            "1. Cannelloni med kött\t\t80:-",
            "2. Cannelloni vegetarisk\t80:-\n",

            "-------------",
            "3. Fortsätt handla",
            "4. Avsluta"
        };

        //Lista på restaurangens drycker
        public static List<string> Drinks = new List<string>
        {
            "Drycker",
            "-------------\n",

            "1. Coca Cola\t20:-",
            "2. Fanta\t20:-",
            "3. Sprite\t20:-",
            "4. Trocadero\t20:-",
            "5. Öl\t\t50:-\n",

            "-------------",
            "6. Fortsätt handla",
            "7. Avsluta"
        };

        //Menyn för "confirmation screen"
        public static List<string> ConfirmationScreen = new List<string>
        {

            "Din beställning är tillagd",
            "-------------\n",

            "1. Fortsätt handla",
            "2. Gå till betalning\n",

            "-------------",
            "3. Avsluta"
        };

        //Menyn för betalningsskärm
        public static List<string> PaymentMenu = new List<string>
        {
            "1. Betala med kort",
            "2. Fortsätt handla\n",

            "-------------",
            "3. Avsluta"
        };
    }
}
