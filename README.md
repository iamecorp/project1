import java.util.*;

public class PhoneBook {
    public static void main(String[] args) {
        Map<String, List<String>> phoneBook = new HashMap<>();

        // Добавление записей в телефонную книгу
        addContact(phoneBook, "Иванов", "123456789");
        addContact(phoneBook, "Петров", "987654321");
        addContact(phoneBook, "Сидоров", "555111222");
        addContact(phoneBook, "Иванов", "999888777");
        addContact(phoneBook, "Петров", "333444555");

        // Вывод телефонной книги с сортировкой по убыванию числа телефонов
        printPhoneBook(phoneBook);
    }

    // Метод для добавления контакта в телефонную книгу
    private static void addContact(Map<String, List<String>> phoneBook, String name, String phoneNumber) {
        // Если имя уже есть в телефонной книге, добавляем телефон к списку
        if (phoneBook.containsKey(name)) {
            List<String> phoneNumbers = phoneBook.get(name);
            phoneNumbers.add(phoneNumber);
        } else {
            // Если имя отсутствует, создаем новую запись
            List<String> phoneNumbers = new ArrayList<>();
            phoneNumbers.add(phoneNumber);
            phoneBook.put(name, phoneNumbers);
        }
    }

    // Метод для вывода телефонной книги с сортировкой по убыванию числа телефонов
    private static void printPhoneBook(Map<String, List<String>> phoneBook) {
        // Создаем список записей из мапы
        List<Map.Entry<String, List<String>>> entries = new ArrayList<>(phoneBook.entrySet());

        // Сортируем записи по убыванию числа телефонов
        entries.sort((entry1, entry2) -> Integer.compare(entry2.getValue().size(), entry1.getValue().size()));

        // Выводим отсортированные записи
        for (Map.Entry<String, List<String>> entry : entries) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
    }
}
