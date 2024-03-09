# Task-5-Java
import java.util.Scanner; 

  

public class Quiz { 

    private Question[] questions; 

    private int score; 

  

    public Quiz(Question[] questions) { 

        this.questions = questions; 

        this.score = 0; 

    } 

  

    public void displayQuestion(int questionNum) { 

        Question question = questions[questionNum]; 

        String questionText = question.getQuestion(); 

        String[] options = question.getOptions(); 

        System.out.println("Question " + (questionNum + 1) + ": " + questionText); 

        for (int i = 0; i < options.length; i++) { 

            System.out.println((i + 1) + ". " + options[i]); 

        } 

    } 

  

    public void submitAnswer(int questionNum, int userAnswer) { 

        Question question = questions[questionNum]; 

        int correctAnswer = question.getAnswer(); 

        if (userAnswer == correctAnswer) { 

            score++; 

        } 

    } 

  

    public void startQuiz() { 

        Scanner scanner = new Scanner(System.in); 

        for (int i = 0; i < questions.length; i++) { 

            displayQuestion(i); 

            long startTime = System.currentTimeMillis(); 

            int userAnswer = scanner.nextInt(); 

            long endTime = System.currentTimeMillis(); 

            double timeTaken = (endTime - startTime) / 1000.0; 

            if (timeTaken > 10) { 

                System.out.println("Time's up! Moving to the next question."); 

                continue; 

            } 

            submitAnswer(i, userAnswer); 

        } 

        System.out.println("\nQuiz completed!"); 

        System.out.println("Your score: " + score + "/" + questions.length); 

        System.out.println("Summary:"); 

        for (int i = 0; i < questions.length; i++) { 

            Question question = questions[i]; 

            System.out.println("Question " + (i + 1) + ": " + (userAnswer == question.getAnswer() ? "Correct" : "Incorrect")); 

        } 

    } 

  

    public static void main(String[] args) { 

        Question[] questions = { 

            new Question("What is the capital of France?", new String[]{"London", "Paris", "Berlin", "Madrid"}, 2), 

            new Question("What is 2 + 2?", new String[]{"3", "4", "5", "6"}, 2) 

        }; 

  

        Quiz quiz = new Quiz(questions); 

        quiz.startQuiz(); 

    } 

} 

  

class Question { 

    private String question; 

    private String[] options; 

    private int answer; 

  

    public Question(String question, String[] options, int answer) { 

        this.question = question; 

        this.options = options; 

        this.answer = answer; 

    } 

  

    public String getQuestion() { 

        return question; 

    } 

  

    public String[] getOptions() { 

        return options; 

    } 

  

    public int getAnswer() { 

        return answer; 

    } 

} 

 

 
