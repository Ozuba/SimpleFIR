# SimpleFIR
This is a simple implementation of a FIR filter i made for real time proccessing on
an STM32F103C8, as it lacks a floating point unit it had to be implemented using only 
integer arithmetics in order to maximize performance.

## Library interface
The library defines a `FIR_t` object which can be created dynamicaly by an 
initialization funcion

## Example usage

```c
#Coefficents
float coeffs[N] = {...}

int main(){
FIR_t * filter;
filt = initFilter(&coeffs,N,xMax); # Coefficents, Order of the Filter (TAPS), Upper bounding for Signal

while(1){
    int x = readSignal();
    int x = filter(filt,x); # Returns filtered signal with a delay of N samples
}

deInitFilter(filter)
return 1;
}
```

## Filter Design
