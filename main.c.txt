#include <stdio.h>
#include <unistd.h>

unsigned int GPIO_PORT = 0;

void set_pin(int pin) {
    GPIO_PORT |= (1 << pin);
}

void clear_pin(int pin) {
    GPIO_PORT &= ~(1 << pin);
}

void display_led(int pin) {
    if (GPIO_PORT & (1 << pin))
        printf("LED ON\n");
    else
        printf("LED OFF\n");
}

int main() {
    int pin = 2;

    while (1) {
        set_pin(pin);
        display_led(pin);
        sleep(1);

        clear_pin(pin);
        display_led(pin);
        sleep(1);
    }

    return 0;
}