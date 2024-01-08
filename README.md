import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class CurrencyConverter {
    private static final String API_BASE_URL = "https://api.exchangerate.host/latest";
    private static final Map<String, Double> exchangeRates = new HashMap<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("1. Add Favorite Currency");
            System.out.println("2. View Favorite Currencies");
            System.out.println("3. Update Favorite Currencies");
            System.out.println("4. Show Exchange Rates");
            System.out.println("5. Exit");

            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    addFavoriteCurrency(scanner);
                    break;
                case 2:
                    viewFavoriteCurrencies();
                    break;
                case 3:
                    updateFavoriteCurrencies(scanner);
                    break;
                case 4:
                    showExchangeRates();
                    break;
                case 5:
                    System.out.println("Exiting. Goodbye!");
                    System.exit(0);
                default:
                    System.out.println("Invalid choice. Try again.");
            }
        }
    }

    private static void addFavoriteCurrency(Scanner scanner) {
        System.out.print("Enter the currency code to add to favorites: ");
        String currencyCode = scanner.next();

        // Add logic to validate currency code and add to favorites
        // You may want to fetch the list of available currencies from the API for validation
    }

    private static void viewFavoriteCurrencies() {
        // Display the list of favorite currencies
    }

    private static void updateFavoriteCurrencies(Scanner scanner) {
        // Update logic for favorite currencies
    }

    private static void showExchangeRates() {
        String exchangeRatesData = getExchangeRates();

        // Parse the exchange rates data and display the rates
        // Update the exchangeRates map with the latest rates
    }

    private static String getExchangeRates() {
        try {
            HttpClient client = HttpClient.newHttpClient();
            HttpRequest request = HttpRequest.newBuilder()
                    .uri(URI.create(API_BASE_URL))
                    .build();

            HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());

            return response.body();
        } catch (Exception e) {
            e.printStackTrace();
            return null;
        }
    }
}
