
### Example 1: Generating UUID

```Java
<div style="background-color: black; color: white; padding: 10px;">
import java.util.Arrays;
import java.util.DoubleSummaryStatistics;
import java.util.stream.DoubleStream;

public class Main {
    public static void main(String[] args) {
        double[] numbers = {1.5, 2.5, 3.5, 4.5, 5.5};

        // Create a sequential DoubleStream for a specific range of the array
        int start = 1;
        int end = 4; // endExclusive means it will cover indices 1, 2, and 3 (not 4)
        
        try {
            DoubleStream stream = stream(numbers, start, end);
            
            // Print elements in the specified range using forEach
            stream.forEach(System.out::println);
            
            // Alternatively, you can collect statistics about the elements in the range
            DoubleSummaryStatistics stats = stream.summaryStatistics();
            System.out.println("Statistics for the range:");
            System.out.println("Sum: " + stats.getSum());
            System.out.println("Average: " + stats.getAverage());
            System.out.println("Min: " + stats.getMin());
            System.out.println("Max: " + stats.getMax());
            
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Error: Invalid range specified.");
        }
    }

    // Implementation of the stream method
    public static DoubleStream stream(double[] array, int startInclusive, int endExclusive) {
        if (startInclusive < 0 || endExclusive < startInclusive || endExclusive > array.length) {
            throw new ArrayIndexOutOfBoundsException("Invalid range specified.");
        }

        return Arrays.stream(array, startInclusive, endExclusive);
    }
}

</div>

