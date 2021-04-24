import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;


class Result {

    /*
     * Complete the 'calculateScore' function below.
     *
     * The function is expected to return a STRING.
     * The function accepts following parameters:
     *  1. STRING text
     *  2. STRING prefixString
     *  3. STRING suffixString
     */

    public static String calculateScore(String text, String prefixString, String suffixString) {
    // Write your code here
    int n = text.length();
        int sl = suffixString.length();
        int pl = prefixString.length();


        Map<String, Integer> map = new HashMap<>();

        for(int i =0; i<n; i++) {
            for(int j = i+1; j<=n; j++) {

                String sub = text.substring(i,j);

                int ps = 0, ss = 0, subL = sub.length();

                for(int k =0; k < subL; k++) {
                    if(subL - k <= sl) {
                        if(sub.substring(k).equals(suffixString.substring(0,subL-k))) {
                            ps = Math.max(subL-k, ps);
                        }
                    }
                }

                for(int k =0; k < subL; k++) {
                    if(k < pl) {
                        if(sub.substring(0,k+1).equals(prefixString.substring(pl-k-1, pl))) {
                            ss = Math.max(k+1,ss);
                        }
                    }
                }

                if(map.get(sub)==null) {
                    map.put(sub, ps+ss);
                } else {
                    map.put(sub, Math.max(map.get(sub), ps+ss));
                }
            }
        }
        int m = -1;
        Set<String> keys = map.keySet();

        String[] arr = keys.toArray(new String[keys.size()]);

        Arrays.sort(arr);
        String ans = null;
        for(int i = 0; i<arr.length; i++) {
            if(m < map.get(arr[i])) {
                ans = arr[i];
                m = map.get(arr[i]);
            }
        }

        return ans;

    }

}
public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        String text = bufferedReader.readLine();

        String prefixString = bufferedReader.readLine();

        String suffixString = bufferedReader.readLine();

        String result = Result.calculateScore(text, prefixString, suffixString);

        bufferedWriter.write(result);
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}
