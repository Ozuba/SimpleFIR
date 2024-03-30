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
float coeffs[N] = {...};

int main(){
FIR_t * filter;
filt = initFilter(&coeffs,N,xMax); // Coefficents, Order of the Filter (TAPS), Upper bounding for Signal

while(1){
    int x = readSignal();
    int x = filter(filt,x); // Returns filtered signal with a delay of N samples
}

deInitFilter(filt);
return 1;
}
```
# Results
The following signal was filtered using this library, take in mind that there is still a quatization noise due to the lack of resolution of the adc at the range of the input signal.
Pre-Filtering             |  After-Filtering
:-------------------------:|:-------------------------:
![image](https://github.com/Ozuba/SimpleFIR/assets/96722632/e32c6b1f-3509-407c-8e2a-2958c7658eca)  |  ![image](https://github.com/Ozuba/SimpleFIR/assets/96722632/a17b4c72-09d9-4a50-9f93-50bcd5a67cf4)




## Filter Design
I recommend to use the awesome work by Christian Münker  with his [pyfda](https://github.com/chipmuenk/pyfda), aswell as to read a bit about how filters really work,
(Laplace/Z-Transform/Transfer-Functions...)
