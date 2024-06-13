# 12-ACD-Switch

The next example shows how to find a numerical value of a hexadecimal digit(0-9 or a-f lower or upper case). Here, we take advantage of the “fall through” feature; note that if ch is any lower case letter from the range [a, f], due to “falling through”, we will end up in line 24 and then break out. The same applies to digits (see lines 26-27):

## Listing 12 ACD-Switch/Switch.java Page 33

```java
import java.util.Scanner;

public class Switch {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.print("Enter a single hex digit -> ");
        char ch = scan.next().charAt(0);
        scan.close();

        // Convert to lower case manually
        if (ch >= 'A' && ch <= 'Z') {
            ch = (char)(ch + 'a' - 'A');
        }

        int num;

        switch (ch) {
            case 'a':
            case 'b':
            case 'c':
            case 'd':
            case 'e':
            case 'f':
                num = 10 + ch - 'a';
                break;
            case '0': case '1': case '2': case '3': case '4':
            case '5': case '6': case '7': case '8': case '9':
                num = ch - '0';
                break;
            default:
                num = -1;
        }

        System.out.println("Character '" + ch + "' is " +
                (num >= 0 ? "" : "not ") + "a hex digit. " +
                "Its numerical value: " + num);
    }
}

```
