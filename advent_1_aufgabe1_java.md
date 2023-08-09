// Press Shift twice to open the Search Everywhere dialog and type `show whitespaces`,
// then press Enter. You can now see whitespace characters in your code.

import java.io.BufferedReader;
import java.io.File;
import java.io.FileReader;
import java.io.IOException;


public class Main {

    public static void ladeDatei(String datName) {


    }


    public static void main(String[] args) {
        String datName = "\\\\service.local\\dfs\\sml\\Home\\Bilge\\Desktop\\JAVA\\advent1.txt";

        int max=0;
        int check=0;
        int cal;
        int elf=0;
        int count=0;

        File file = new File(datName);

        if (!file.canRead() || !file.isFile())
            System.exit(0);

        BufferedReader in = null;
        try {
            in = new BufferedReader(new FileReader(datName));
            String zeile = null;
            while ((zeile = in.readLine()) != null) {

                if (zeile.isEmpty()){ //Max Kalore finden
                   count++;
                    if (check > max){
                        elf =count;
                        max=check;
                    }

                    check=0;
                }else {
                    cal = Integer.parseInt(zeile);
                    check =check+cal;
                }

            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (in != null)
                try {
                    System.out.println(elf +". Elf trägt meist Kalorie in Höhe von " + max);
                    in.close();
                } catch (IOException e) {
                }
        }

    }
}
