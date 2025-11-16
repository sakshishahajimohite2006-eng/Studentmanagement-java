import java.util.*;

class Student {
    int roll;
    String name;
    String cor;

    Student(int roll, String name, String cor) {
        this.roll = roll;
        this.name = name;
        this.cor = cor;
    }

    void disp() {
        System.out.println("Name: " + name);
        System.out.println("Roll: " + roll);
        System.out.println("Course: " + cor);
        
    }
}

class Studentsystem {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        Student[] students = new Student[100];
        int count = 0;
        int opt;

        while (true) {
            System.out.println("\nEnter the option");
            System.out.println("1. Add Student Detail");
            System.out.println("2. View Student Detail");
            System.out.println("3. Delete Student Detail");
            System.out.println("4. Exit");
            System.out.print("Option: ");
            opt = sc.nextInt();
            sc.nextLine();

            switch (opt) {
                case 1:
                    System.out.println("#### Adding Student Details ####");
                    System.out.print("Enter the name of student: ");
                    String name = sc.nextLine();
                    System.out.print("Enter the roll number: ");
                    int roll = sc.nextInt();
                    sc.nextLine();
                    System.out.print("Enter the course name: ");
                    String cor = sc.nextLine();
                    students[count] = new Student(roll, name, cor);
                    count++;
                    System.out.println("Detail Added Successfully!");
                    break;

                case 2:
                    System.out.println("---- Student List ----");
                    if (count == 0)
                    {
                        System.out.println("No student to display");
                    }
                    else
                    {
                        for (int i = 0; i < count; i++)
                        {
                            students[i].disp();
                        }
                    }
                    break;

                case 3:
                    System.out.print("Enter the roll no to delete: ");
                    int deleteRoll = sc.nextInt();
                    boolean found = false;
                    for (int i = 0; i < count; i++) 
                    {
                        if (students[i].roll == deleteRoll)
                         {
                            for (int j = i; j < count - 1; j++) 
                            {
                                students[j] = students[j + 1];
                            }
                            students[count - 1] = null;
                            count--;
                            found = true;
                            System.out.println("Student deleted successfully!");
                            break;
                        }
                    }
                    

                case 4:
                    System.out.println("Exiting...");
                    return;

                default:
                    System.out.println("Invalid Option!");
            }
        }
    }
}
