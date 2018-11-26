# quiz-grading
Serves as an aid to grading a 10 question multiple choice quiz. 

    import java.util.Scanner;
    public class quizGrader {
      public static void main(String[] args) {
        //Declare and initialize an array with correct answers
        String[] answerKey = {"a", "b", "c", "d", "b", "d", "c", "c", "b", "a"};
        String[] studentAnswers = new String[10];
        //Call readResponse
        readResponse(studentAnswers);
        //Call gradeResponse
        int grade = gradeResponse(studentAnswers, answerKey);
        //Call didPass
        boolean didPass = didPass(studentAnswers, answerKey);
        //Print whether or not the student has passed (true/false).
        System.out.println("The student has passed! " + didPass);
        //If the student passed, print the grade.
        if (didPass) {
            System.out.println("And the grade passed with is: " + grade);
        }
    }

    /**
     * This method reads in values, serving as the student's answers, and stores them in an array.
     * @param studentAnswers is the array in which the input will be stored.
     */
    public static void readResponse(String studentAnswers[]) {
        System.out.println("Enter the answers for questions 1-10: ");
        Scanner sc = new Scanner(System.in);
        for (int i = 0; i < studentAnswers.length; i++) {
            studentAnswers[i] = sc.nextLine();
        }
    }

    /**
     * This method compares the student's answers to the answer key in order to determine the grade.
     * @param studentAnswers is the array holding the student's answers.
     * @param answerKey is the array holding the correct answers.
     * @return the student's grade.
     */
    public static int gradeResponse(String studentAnswers[], String answerKey[]) {
        int grade = 0;
        for (int i = 0; i < answerKey.length; i++) {
            if (answerKey[i].equals(studentAnswers[i])) {
                grade += 10;
            }
        }
        return grade;
    }

    /**
     * This method determines whether or not the student has passed based on a passing grade
     * of 6 or more correct answers.
     * @param studentAnswers is the array holding the student's answers.
     * @param answerKey is the array holding the correct answers, to be compared to the student's answers.
     * @return true if the student had 6 or more correct answers, and false if otherwise.
     */
    public static boolean didPass(String studentAnswers[], String answerKey[]) {
        int correctAnswers = 0;
        for (int i = 0; i < answerKey.length; i++) {
            if (answerKey[i].equals(studentAnswers[i])) {
                correctAnswers++;
            }
        }
        return correctAnswers >= 6;
     }
    }
