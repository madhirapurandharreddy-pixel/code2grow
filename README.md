#include <stdio.h>

int main()
{
    int customers, items, i, j, qty, feedback;
    float price, subtotal, gst, finalBill;
    float totalRevenue = 0, highestBill = 0;
    float totalFeedback = 0;

    printf("Enter number of customers: ");
    scanf("%d", &customers);

    for (i = 1; i <= customers; i++)
    {

        printf("\nCustomer %d:\n", i);
        printf("Enter number of items: ");
        scanf("%d", &items);

        subtotal = 0;

        for (j = 1; j <= items; j++)
        {
            printf("Enter price of item %d: ", j);
            scanf("%f", &price);
            printf("Enter quantity: ");
            scanf("%d", &qty);

            subtotal += price * qty;
        }

        gst = subtotal * 0.05;
        finalBill = subtotal + gst;

        printf("Enter feedback (1–5): ");
        scanf("%d", &feedback);

        while (feedback < 1 || feedback > 5)
        {
            printf("Invalid! Enter feedback (1–5): ");
            scanf("%d", &feedback);
        }

        printf("Customer %d Bill: ₹%.2f\n", i, finalBill);

        totalRevenue += finalBill;
        totalFeedback += feedback;

        if (finalBill > highestBill)
        {
            highestBill = finalBill;
        }
    }

    printf("\n--- Restaurant Bill Summary ---\n");
    printf("Total Revenue Today: ₹%.2f\n", totalRevenue);
    printf("Average Feedback Rating: %.2f\n", totalFeedback / customers);
    printf("Highest Bill Amount: ₹%.2f\n", highestBill);

    return 0;
}
