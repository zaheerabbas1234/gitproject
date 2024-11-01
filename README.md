package com.password;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

@SpringBootApplication
public class JdbcApplication {

    public static void main(String[] args) throws ClassNotFoundException, SQLException {
        SpringApplication.run(JdbcApplication.class, args);
        runDatabaseQuery();  // Call the method to run the database query
    }

    private static void runDatabaseQuery() throws ClassNotFoundException, SQLException {
        
                 Class.forName("oracle.jdbc.driver.OracleDriver");

            // Establish a connection to the database
                 Connection connection = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe", "zaheer", "abbas");
                 Statement stmt = connection.createStatement();
                 ResultSet rs = stmt.executeQuery("SELECT * FROM Student");

                // Process the ResultSet
                while (rs.next()) {
                    // Retrieve data from each column
                    int stdRollNo = rs.getInt("STD_ROLL_NO");
                    String course = rs.getString("COURSE");
                    String grade = rs.getString("GRADE");
                    int hibernate = rs.getInt("HIBERNATE");
                    String name = rs.getString("NAME");
                    float percentage = rs.getFloat("PERCENTAGE");
                    String result = rs.getString("RESULT");
                    int spring = rs.getInt("SPRING");
                    int springBoot = rs.getInt("SPRINGBOOT");
                    int total = rs.getInt("TOTAL");

                    // Print the data
                    System.out.println("Roll No: " + stdRollNo +
                            ", Course: " + course +
                            ", Grade: " + grade +
                            ", Hibernate: " + hibernate +
                            ", Name: " + name +
                            ", Percentage: " + percentage +
                            ", Result: " + result +
                            ", Spring: " + spring +
                            ", Spring Boot: " + springBoot +
                            ", Total: " + total);
                }
            
}

}
