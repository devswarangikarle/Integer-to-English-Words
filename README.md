def numberToWords(num):
    if num == 0:
        return "Zero"

    below_twenty = ["", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine", "Ten",
                    "Eleven", "Twelve", "Thirteen", "Fourteen", "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Nineteen"]

    tens = ["", "", "Twenty", "Thirty", "Forty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninety"]

    def helper(n):
        if n == 0:
            return ""
        elif n < 20:
            return below_twenty[n] + " "
        elif n < 100:
            return tens[n // 10] + " " + helper(n % 10)
        else:
            return below_twenty[n // 100] + " Hundred " + helper(n % 100)

    billion = num // 1000000000
    million = (num % 1000000000) // 1000000
    thousand = (num % 1000000) // 1000
    remainder = num % 1000

    result = ""

    if billion > 0:
        result += helper(billion) + "Billion "

    if million > 0:
        result += helper(million) + "Million "

    if thousand > 0:
        result += helper(thousand) + "Thousand "

    result += helper(remainder)

    return result.strip()

# Input
num = int(input())

# Output
print(numberToWords(num))
