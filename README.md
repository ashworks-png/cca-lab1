# cca-lab1

Task 1:
D:
cd <directory-name>
git clone https://github.com/ashworks-png/cca-lab1.git
git status
git add .  OR git add sample.txt
git commit -m "initial commit"
git push origin main
get fetch origin
get pull origin main
git branch a1
git branch
git branch -M a1
git checkout -b a2
git checkout a1 #to switch branches
git reset --soft a1
git branch -d a1 #to delete a1 branch
git rm <file-name> #to delete a file from repo


Task 3:
go to: console.cloud.google.com
enable API -> search 'App Engine Admin API'
open terminal (top-right)

Inside terminal:
git clone https://github.com/ashworks-png/cca-lab1.gi
cd cca-lab1
python3 -m http.server 8000

Task 4:
fcfc-code.java ->
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter number of processes: ");
        int n = scanner.nextInt();

        int[] arrivalTime = new int[n];
        int[] burstTime = new int[n];
        int[] completionTime = new int[n];
        int[] turnaroundTime = new int[n];
        int[] waitingTime = new int[n];

        // Input arrival times and burst times
        for (int i = 0; i < n; i++) {
            System.out.print("Enter arrival time for process " + (i + 1) + ": ");
            arrivalTime[i] = scanner.nextInt();
            System.out.print("Enter burst time for process " + (i + 1) + ": ");
            burstTime[i] = scanner.nextInt();
        }

        // Calculate completion time for each process
        completionTime[0] = arrivalTime[0] + burstTime[0];
        for (int i = 1; i < n; i++) {
            completionTime[i] = completionTime[i - 1] + burstTime[i];
        }

        // Calculate turnaround time and waiting time for each process
        for (int i = 0; i < n; i++) {
            turnaroundTime[i] = completionTime[i] - arrivalTime[i];
            waitingTime[i] = turnaroundTime[i] - burstTime[i];
        }

        // Calculate average turnaround time and average waiting time
        double avgTurnaroundTime = 0;
        double avgWaitingTime = 0;
        for (int i = 0; i < n; i++) {
            avgTurnaroundTime += turnaroundTime[i];
            avgWaitingTime += waitingTime[i];
        }
        avgTurnaroundTime /= n;
        avgWaitingTime /= n;

        // Display results
        System.out.println("\nProcess\t Arrival Time\t Burst Time\t Completion Time\t Turnaround Time\t Waiting Time");
        for (int i = 0; i < n; i++) {
            System.out.println((i + 1) + "\t\t " + arrivalTime[i] + "\t\t " + burstTime[i] + "\t\t " + completionTime[i]
                    + "\t\t " + turnaroundTime[i] + "\t\t " + waitingTime[i]);
        }
        System.out.println("\nAverage Turnaround Time: " + avgTurnaroundTime);
        System.out.println("Average Waiting Time: " + avgWaitingTime);

        scanner.close();
    }
}
