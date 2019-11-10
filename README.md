# PizzaPalatset
namespace CustomerTerminal
{
    class Menu
    {
        public bool correctKey { get; set; }

        char key;

        public Menu() { }

        public Menu(bool correctKey) { this.correctKey = correctKey; }

        // Startskärm som visas om beställning ej påbörjats eller om programmet avslutas
        // Om användaren klickar Enter skickas denne vidare maträttsmenyn
        public void drawStart()
        {

            while (correctKey == false)
            {
                Console.Clear();
                Console.WriteLine("Hej och välkommen till Pizza palatset. \nKlicka på Enter för att påbörja din beställning.");
                key = Console.ReadKey(true).KeyChar;
                if (key == 13)
                {
                    drawFoodMenu(false);
                    correctKey = true;
                }
            }
        }

        // Ritar ut de olika typerna av maträtter som restaurangen erbjuder
        // Kontrollerar också vilket val som användaren gör och skriver ut den meny som användaren vill se
        public void drawFoodMenu(bool correctKey)
        {
            this.correctKey = correctKey;

            while (correctKey == false)
            {
                key = Console.ReadKey(true).KeyChar;
                switch (key)
                {
                    case '1':
                        drawPizzaMenu();
                        correctKey = true;
                        break;

                    case '2':
                        drawPastaMenu();
                        correctKey = true;
                        break;
                    case '3':
                        drawSaladMenu();
                        correctKey = true;
                        break;

                    case '4':
                        drawStart();
                        correctKey = true;
                        break;

                    default:
                        Console.Clear();
                        Console.WriteLine("Välj den typ av mat som du vill beställa:\n");
                        Console.WriteLine("1. Pizza");
                        Console.WriteLine("2. Pasta");
                        Console.WriteLine("3. Sallad\n");
                        Console.WriteLine("4. Gå tillbaka");
                        continue;
                }
            }
        }
 
        // Ritar ut de olika pizzorna som finns på resturangen
        public void drawPizzaMenu()
        {
            Console.Clear();
            Console.WriteLine("5. Avsluta beställning");
        }

        // Ritar ut de olika pastorna som finns på resturangen
        public void drawPastaMenu()
        {
            Console.Clear();
            Console.WriteLine("5. Avsluta beställning");
        }

        // Ritar ut de olika salladerna som finns på resturangen
        public void drawSaladMenu()
        {
            Console.Clear();
            Console.WriteLine("5. Avsluta beställning");
        }

    }
