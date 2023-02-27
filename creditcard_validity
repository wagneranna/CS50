#include <cs50.h>
#include <stdio.h>

int calculate_checksum(long number);
string check_type(long number);

int main(void)
{
    long number = get_long("Number: ");
    int checksum = calculate_checksum(number);
    string type;

    // if checksum is valid determine card type, else invalid
    if (checksum % 10 == 0)
    {
        type = check_type(number);
    }
    else
    {
        type = "INVALID";
    }

    printf("%s\n", type);
}

int calculate_checksum(long number)
{
    int checksum = 0;
    int temp;

    // add each digit and double every second digit
    while (number)
    {
        temp = number % 10;
        checksum += temp;
        number /= 10;

        temp = (number % 10) * 2;
        if (temp > 9)
        {
            temp -= 9;
        }
        checksum += temp;
        number /= 10;
    }

    return checksum;
}

string check_type(long number)
{
    long digit1 = number;
    long digit12 = number;
    string type;

    // get first two digits to check for card type
    while (digit1 >= 10)
    {
        digit1 /= 10;
    }
    while (digit12 >= 100)
    {
        digit12 /= 10;
    }

    // check for card type
    if (number > 1000000000000000)
    {
        if (digit1 == 4)
        {
            type = "VISA";
        }
        else if (digit12 == 51 || digit12 == 52 || digit12 == 53 || digit12 == 54 || digit12 == 55)
        {
            type = "MASTERCARD";
        }
        else
        {
            type = "INVALID";
        }
    }
    else if (number > 100000000000000 && (digit12 == 34 || digit12 == 37))
    {
        type = "AMEX";
    }
    else if (number > 1000000000000 && digit1 == 4)
    {
        type = "VISA";
    }
    else
    {
        type = "INVALID";
    }

    return type;
}
