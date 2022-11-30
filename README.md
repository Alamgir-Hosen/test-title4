import java.io.*;
import java.text.*;
import java.util.*;

public class StudentList {
    public static BufferedReader getBufferedReader(){
        try{
            BufferedReader bufferedReader = new BufferedReader(
                    new InputStreamReader(
                            new FileInputStream("students.txt")));
        }catch (FileNotFoundException e){
            e.printStackTrace();
        }
        return null;
    }
    public static BufferedWriter getBufferedWriter(){
        try {
            BufferedWriter bufferedWriter = new BufferedWriter(
                    new FileWriter("students.txt", true));
             return  bufferedWriter;
        }catch (Exception e){
            System.out.println(e);
        }
        return  null;
    }
    public static void main(String[] args) {

  //            Check arguments
        if (args[0].equals("a")) {
            System.out.println("Loading data ...");
            try {
               BufferedReader bufferedReader = getBufferedReader();
                String line = bufferedReader.readLine();
                String studentNames[] = line.split(",");
                for (String studentName : studentNames) {
                    System.out.println(studentName.trim());
                }
            } catch (Exception e) {
            }
            System.out.println("Data Loaded.");
        } else if (args[0].equals("r")) {
            System.out.println("Loading data ...");
            try {
                            BufferedReader bufferedReader = getBufferedReader();
                String line = bufferedReader.readLine();
                String studentNames[] = line.split(",");
                Random random = new Random();
                int studentNumber = random.nextInt(4);
                System.out.println(studentNames[studentNumber].trim());
            } catch (Exception e) {
            }
            System.out.println("Data Loaded.");
        } else if (args[0].contains("+")) {
            System.out.println("Loading data ...");
            try {
                            BufferedWriter bufferedWriter = getBufferedWriter();

                String newStudentName = args[0].substring(1);
                Date date = new Date();
                String dateFormate = "dd/MM/yyyy-hh:mm:ss a";
                DateFormat dateFormat = new SimpleDateFormat(dateFormate);
                String fd = dateFormat.format(date);
                bufferedWriter.write(", " + newStudentName + "\nList last updated on " + fd);
                bufferedWriter.close();
            } catch (Exception e) {
            }
            System.out.println("Data Loaded.");
        } else if (args[0].contains("?")) {
            System.out.println("Loading data ...");
            try {
                BufferedReader bufferedReader = getBufferedReader();
                String line = bufferedReader.readLine();
                if (line.contains(args[0].substring(1))) {
                    System.out.println("We Found it");
                } else {
                    System.out.println("Not found");
                }
            } catch (Exception e) {
            }
            System.out.println("Data Loaded.");
        } else if (args[0].contains("c")) {
            System.out.println("Loading data ...");
            try {
                            BufferedReader bufferedReader = getBufferedReader();
                String line = bufferedReader.readLine();
                String names[] = line.split(",");
                System.out.println(names.length / 2 + " words found");
            } catch (Exception e) {
            }
            System.out.println("Data Loaded.");
        }
        else{
            System.out.println("Usage:a|c|r|+Studenti|?StudentI");
        }
    }
}
