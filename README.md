# PizzaPalatset
hallå hallå
namespace CustomerTerminal
{
    class Order
    {
        public bool correctKey { get; set; }

        char key;
        int price = 0;
        string bottom;

        // Startskärm som visas om beställning ej påbörjats eller om programmet avslutas
        // Om användaren klickar Enter skickas denne vidare maträttsmenyn
        public void drawStart()
        {

            // För varje gång som en ny order startas eller som programmet avslutas så nollställs alla orderparametrar
            Lists.CurrentOrder.Clear();
            price = 0;

            while (correctKey == false)
            {
                Console.Clear();
                Console.WriteLine("Hej och välkommen till Pizza palatset. \nKlicka på Enter för att påbörja din beställning.");
                key = Console.ReadKey(true).KeyChar;
                if (key == 13)
                {
                    drawFoodMenu();
                    correctKey = true;
                }
            }
        }

        // Ritar ut de olika typerna av maträtter som restaurangen erbjuder
        // Kontrollerar också vilket val som användaren gör och skriver ut den meny som användaren vill se
        public void drawFoodMenu()
        {
            Console.Clear();
            foreach (string lines in Lists.FoodMenu)
            {
                Console.WriteLine(lines);
            }

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
                        drawDrinkMenu();
                        correctKey = true;
                        break;

                    case '5': // Om listan med ordrar är tom kommer man tillbaka till startskärm
                        if (Lists.CurrentOrder.Count == 0)
                        {
                            Console.Clear();
                            Console.WriteLine("\nIngen order lagt ännu");
                            System.Threading.Thread.Sleep(2000);
                            drawFoodMenu();
                        }
                        else
                        {
                            drawCurrentOrder();
                            correctKey = true;
                        }
                        break;

                    case '6':
                        drawStart();
                        correctKey = true;
                        break;

                    default:

                        Console.Clear();
                        foreach (string lines in Lists.FoodMenu)
                        {
                            Console.WriteLine(lines);
                        }

                        continue;
                }
            }
        }

        // Ritar ut de olika pizzorna som finns på resturangen
        public void drawPizzaMenu()
        {
            Console.Clear();
            foreach (string choices in Lists.Pizzas)
            {
                Console.WriteLine(choices);
            }

            while (correctKey == false)
            {
                key = Console.ReadKey(true).KeyChar;
                switch (key)
                {
                    case '1':

                        drawPizzaBottomMenu("Vesuvio");
                        correctKey = true;
                        break;
                    case '2':

                        drawPizzaBottomMenu("Margarita");
                        correctKey = true;
                        break;

                    case '3':

                        drawPizzaBottomMenu("Hawaii");
                        correctKey = true;
                        break;

                    case '4':

                        drawPizzaBottomMenu("Calzone");
                        correctKey = true;
                        break;

                    case '5': //Återgå till maträttsmenyn
                        drawFoodMenu();
                        correctKey = true;
                        break;

                    case '6': //Avsluta
                        drawStart();
                        correctKey = true;
                        break;

                    default:

                        Console.Clear();
                        foreach (string choices in Lists.Pizzas)
                        {
                            Console.WriteLine(choices);
                        }

                        continue;

                }
            }
        }

        // Ritar ut och behandlar användares val av pizzabotten
        public void drawPizzaBottomMenu(string pizza)
        {
            Console.Clear();
            foreach (string choices in Lists.PizzaBottoms)
            {
                Console.WriteLine(choices);
            }

            while (correctKey == false)
            {
                key = Console.ReadKey(true).KeyChar;
                switch (key)
                {
                    case '1':
                        bottom = ", Italiensk botten";
                        Lists.CurrentOrder.Add(pizza + bottom);
                        price += 80; //Lägger till 80 kr på det totala priset
                        drawExtras();
                        correctKey = true;
                        break;

                    case '2':
                        bottom = ", Amerikansk botten";
                        Lists.CurrentOrder.Add(pizza + bottom);
                        price += 80; //Lägger till 80 kr på det totala priset
                        drawExtras();
                        correctKey = true;
                        break;


                    case '3': //Återgå till Pizzameny
                        drawPizzaMenu();
                        correctKey = true;
                        break;

                    case '4': //Avsluta
                        drawStart();
                        correctKey = true;
                        break;

                    default:

                        Console.Clear();
                        foreach (string choices in Lists.PizzaBottoms)
                        {
                            Console.WriteLine(choices);
                        }

                        continue;
                }
            }
        }

        // Ritar ut de olika pastorna som finns på resturangen
        public void drawPastaMenu()
        {
            Console.Clear();
            foreach (string choices in Lists.Pastas)
            {
                Console.WriteLine(choices);
            }

            while (correctKey == false)
            {
                key = Console.ReadKey(true).KeyChar;
                switch (key)
                {
                    case '1':
                        Lists.CurrentOrder.Add("Cannelloni med kött");
                        price += 80;
                        drawConfirmationScreen();
                        correctKey = true;
                        break;

                    case '2':
                        Lists.CurrentOrder.Add("Cannelloni vegetarisk");
                        price += 80;
                        drawConfirmationScreen();
                        correctKey = true;
                        break;

                    case '3':
                        drawFoodMenu(); //Fortsätt handla
                        correctKey = true;
                        break;

                    case '4': //Återgå till maträttsmenyn
                        drawStart();
                        correctKey = true;
                        break;

                    default:
                        Console.Clear();
                        foreach (string choices in Lists.Salads)
                        {
                            Console.WriteLine(choices);
                        }
                        continue;
                }
            }
        }

        // Ritar ut de olika salladerna som finns på resturangen
        public void drawSaladMenu()
        {
            Console.Clear();
            foreach (string choices in Lists.Salads)
            {
                Console.WriteLine(choices);
            }

            while (correctKey == false)
            {
                key = Console.ReadKey(true).KeyChar;
                switch (key)
                {
                    case '1':
                        Lists.CurrentOrder.Add("Mozarellasallad");
                        price += 80;
                        drawConfirmationScreen();
                        correctKey = true;
                        break;

                    case '2':
                        Lists.CurrentOrder.Add("Chevresallad");
                        price += 80;
                        drawConfirmationScreen();
                        correctKey = true;
                        break;

                    case '3':
                        drawFoodMenu(); //Fortsätt handla
                        correctKey = true;
                        break;

                    case '4': //Återgå till maträttsmenyn
                        drawStart();
                        correctKey = true;
                        break;
                        
                    default:
                        Console.Clear();
                        foreach (string choices in Lists.Salads)
                        {
                            Console.WriteLine(choices);
                        }
                        continue;
                }
            }
        }

        //Skriver ut dryckesmenyn
        public void drawDrinkMenu()
        {
            Console.Clear();
            foreach(string drinks in Lists.Drinks)
            {
                Console.WriteLine(drinks);
            }

            while (correctKey == false)
            {
                key = Console.ReadKey(true).KeyChar;
                switch (key)
                {
                    case '1':
                        Lists.CurrentOrder.Add("Coca Cola");
                        price += 20;
                        drawConfirmationScreen();
                        correctKey = true;
                        break;

                    case '2':
                        Lists.CurrentOrder.Add("Fanta");
                        price += 20;
                        drawConfirmationScreen();
                        correctKey = true;
                        break;

                    case '3':
                        Lists.CurrentOrder.Add("Sprite");
                        price += 20;
                        drawConfirmationScreen();
                        correctKey = true;
                        break;

                    case '4':
                        Lists.CurrentOrder.Add("Trocadero");
                        price += 20;
                        drawConfirmationScreen();
                        correctKey = true;
                        break;

                    case '5':
                        Lists.CurrentOrder.Add("Öl");
                        price += 50;
                        drawConfirmationScreen();
                        correctKey = true;
                        break;

                    case '6':
                        drawFoodMenu();
                        correctKey = true;
                        break;

                    case '7':
                        drawStart();
                        correctKey = true;
                        break;

                    default:
                        Console.Clear();
                        foreach (string drinks in Lists.Drinks)
                        {
                            Console.WriteLine(drinks);
                        }
                        continue;
                }
            }
        }

        // Visar användarens pågående order
        public void drawCurrentOrder()
        {
            Console.Clear();

            Console.WriteLine("Din beställning:");
            Console.WriteLine("-------------\n");

            foreach (string orders in Lists.CurrentOrder)
            {
                Console.WriteLine(orders);
            }

            Console.WriteLine($"\nTotal kostnad: {price}:-");

            Console.WriteLine("\n-------------\n");

            foreach (string items in Lists.CurrentOrderMenu)
            {
                Console.WriteLine(items);
            }

            while (correctKey == false)
            {
                key = Console.ReadKey(true).KeyChar;
                switch (key)
                {
                    case '1':
                        drawPayment();
                        correctKey = true;
                        break;

                    case '2':
                        drawFoodMenu();
                        correctKey = true;
                        break;

                    case '3':
                        drawRemoveOrder();
                        correctKey = true;
                        break;

                    case '4':
                        drawStart();
                        correctKey = true;
                        break;


                    default:
                        Console.Clear();

                        Console.WriteLine("Din beställning:");
                        Console.WriteLine("-------------\n");

                        foreach (string orders in Lists.CurrentOrder)
                        {
                            Console.WriteLine(orders);
                        }

                        Console.WriteLine($"\nTotal kostnad: {price}:-");

                        Console.WriteLine("\n-------------\n");

                        foreach (string items in Lists.CurrentOrderMenu)
                        {
                            Console.WriteLine(items);
                        }
                        continue;
                }
            }
        }


        // Ritar ut betalningsterminal
        public void drawPayment()
        {
            Console.Clear();
            Console.WriteLine("Din beställning:");
            Console.WriteLine("-------------\n");

            foreach (string orders in Lists.CurrentOrder)
            {
                Console.WriteLine(orders);
            }

            Console.WriteLine($"\nTotal kostnad: {price}:-");
            Console.WriteLine("\n-------------\n");

            foreach(string lines in Lists.PaymentMenu)
            {
                Console.WriteLine(lines);
            }

            while (correctKey == false)
            {
                key = Console.ReadKey(true).KeyChar;
                switch (key)
                {
                    case '1':
                        bool payment = Payment.Pay(); //Om kund väljer att betala körs en funktion som kontrollerar att betalningen är godkänd
                        Console.Clear();
                        Console.WriteLine("Din betalning behandlas...");
                        System.Threading.Thread.Sleep(1000);
                        if (payment == true)
                        {
                            Console.Clear();
                            drawReceipt();
                        }
                        else if(payment == false)
                        {
                            Console.Clear();
                            Console.WriteLine("Din betalning godkändes inte, du skickas nu tillbaka till betalningsskärmen...");
                            System.Threading.Thread.Sleep(2000);
                            Console.Clear();
                            drawPayment();
                        }
                        correctKey = true;
                        break;

                    case '2':
                        drawFoodMenu(); //Fortsätt handla
                        correctKey = true;
                        break;

                    case '3':
                        drawStart(); // Avsluta
                        correctKey = true;
                        break;

                    default:
                        Console.Clear();
                        Console.WriteLine("Din beställning:");
                        Console.WriteLine("-------------\n");

                        foreach (string orders in Lists.CurrentOrder)
                        {
                            Console.WriteLine(orders);
                        }

                        Console.WriteLine($"\nTotal kostnad: {price}:-");
                        Console.WriteLine("\n-------------\n");

                        foreach (string lines in Lists.PaymentMenu)
                        {
                            Console.WriteLine(lines);
                        }

                        continue;
                }
            }
        }
        public void drawExtras()
        {
            Console.Clear();
            string currentOrder = Lists.CurrentOrder[Lists.CurrentOrder.Count - 1];
            Console.WriteLine(currentOrder);
            Console.WriteLine("\n-------------\n");
            Console.WriteLine("1. Lägg till orderbeställning");
            Console.WriteLine("2. Lägg till extra ingrediens");
            Console.WriteLine("3. Ta bort ingrediens");
            Console.WriteLine("4. Gå tillbaka");
            key = Console.ReadKey(true).KeyChar;

            switch(key)
            {
                case '1':
                    drawConfirmationScreen();
                    break;

                case '2':
                    drawAddPieces();
                    break;

                case '3':
                    drawRemovePieces();
                    break;

                case '4':
                    Lists.CurrentOrder.RemoveAt(Lists.CurrentOrder.Count - 1);
                    price = price - 80;
                    drawPizzaMenu();
                    break;

            }
        }
        //Ritar ut tillgängliga extra ingredienser och lägger till användarens val
        public void drawAddPieces()
        {
            Console.Clear();
            Console.WriteLine("Välj tillägg, 5kr styck\n");
            Console.WriteLine("1. Ost");
            Console.WriteLine("2. Mozzarella");
            Console.WriteLine("3. Ädelost");
            Console.WriteLine("4. Skinka");
            Console.WriteLine("5. Salami");
            Console.WriteLine("6. Lök");
            Console.WriteLine("7. Oliver");
            Console.WriteLine("8. Ananas");
            Console.WriteLine("9. Curry");
            key = Console.ReadKey(true).KeyChar;

            switch (key)
            {
                case '1':
                    Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] = Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] + " \n+ Ost";
                    price += 5;
                    drawExtras();
                    break;
                case '2':
                    Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] = Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] + " \n+ Mozzarella";
                    price += 5;
                    drawExtras();
                    break;
                case '3':
                    Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] = Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] + "\n+ Ädelost";
                    price += 5;
                    drawExtras();
                    break;
                case '4':
                    Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] = Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] + "\n+ Skinka";
                    price += 5;
                    drawExtras();
                    break;
                case '5':
                    Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] = Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] + "\n+ Salami";
                    price += 5;
                    drawExtras();
                    break;
                case '6':
                    Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] = Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] + "\n+ Lök";
                    price += 5;
                    drawExtras();
                    break;
                case '7':
                    Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] = Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] + "\n+ Oliver";
                    price += 5;
                    drawExtras();
                    break;
                case '8':
                    Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] = Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] + "\n+ Ananas";
                    price += 5;
                    drawExtras();
                    break;
                case '9':
                    Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] = Lists.CurrentOrder[Lists.CurrentOrder.Count - 1] + "\n+Curry";
                    price += 5;
                    drawExtras();
                    break;
                default:
                    drawAddPieces();
                    break;
            }

        }
        // Ritar ut nuvarande order med nummer och låter användaren välja vilken som ska tas bort
        public void drawRemoveOrder()
        {
            Console.Clear();
            Console.WriteLine("Vilken order vill du ta bort?");
            Console.WriteLine("-------------\n");

            for (int i = 0; i < Lists.CurrentOrder.Count;i++)
            {
                Console.WriteLine($"{i+1}.{Lists.CurrentOrder[i]}");
            }
            Console.WriteLine("-------------\n");

            key = Console.ReadKey(true).KeyChar;
            int index = key-'0';
            try
            {
                Lists.CurrentOrder.RemoveAt(index - 1);
                price = price - 80;
                if (Lists.CurrentOrder.Count == 0)
                {
                    Console.Clear();
                    drawFoodMenu();
                }
                else
                {
                    drawCurrentOrder();
                    correctKey = true;
                }
            }
            catch(Exception)
            {
                drawRemoveOrder();
            }
        }
        // TODO
        public void drawRemovePieces()
        {
            Console.Clear();
            Console.WriteLine("Denna del är under bearbetning...");
            Console.WriteLine("1. Gå tillbaka");
            if(key == 1)
            {
                drawFoodMenu();
            }
        }

        // skärm som skrivs ut när en beställning lagts
        public void drawConfirmationScreen()
        {
            Console.Clear();
            foreach (string lines in Lists.ConfirmationScreen)
            {
                Console.WriteLine(lines);
            }

            while (correctKey == false)
            {
                key = Console.ReadKey(true).KeyChar;
                switch (key)
                {
                    case '1':
                        drawFoodMenu(); //Fortsätt handla
                        correctKey = true;
                        break;

                    case '2':
                        drawPayment(); //Gå till betalning
                        correctKey = true;
                        break;

                    case '3':
                        drawStart(); // Avsluta
                        correctKey = true;
                        break;

                    default:

                        Console.Clear();
                        foreach (string lines in Lists.ConfirmationScreen)
                        {
                            Console.WriteLine(lines);
                        }

                        continue;
                }
            }

        }

        // funktion som skapar ett random ordernumer till kunden
        private int OrderNumber()
        {
            Random ordernumber = new Random();

            return ordernumber.Next(1, 100);
        }

        //skriver ut kvitto
        public void drawReceipt()
        {
            Console.WriteLine("Tack för din betalning!");
            Console.WriteLine("-------------\n");
            
            foreach(string orders in Lists.CurrentOrder)
            {
                Console.WriteLine(orders);
            }

            Console.WriteLine($"\nKostnad: {price}:-\n");
            Console.WriteLine("-------------\n");
            Console.WriteLine($"Ditt ordernummer är {OrderNumber()}");

            // Programmet startas automatiskt om 10 sekunder efter att kunden tagit emot sitt kvitto
            System.Threading.Thread.Sleep(8000);
            drawStart();
        }
    }
