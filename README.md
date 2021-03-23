# runningAverage

Lightweight running average library for the Arduino Platform

To use it you'll need to first define the size of your running average and the type of the class:

```cpp
#define RA_SIZE N
RunningAverage<T> RA_M(RA_SIZE);
```

Where T can be any numeric data type and N is a positive integer.

Before using it's adiviced to fill all values with a more convenient one. To do it use the fillValue function (the default value is 0).

```cpp
RA_M.fillValue(T value, int number);
```

It fills the average with a value the param number determines how often value is added (weight) number should preferably be between 1 and size.

Finaly the running average can be used as follow:

```cpp
RA_M.addValue(T value);
T variable = RA_M.getAverage(T value);
```

In a pratical example:

```cpp
//RunningAverage size for the encoder
#define RA_SIZE 4
RunningAverage<int> RA_M(RA_SIZE);

void setup() {
    RA_M.fillValue(0, RA_SIZE);
}

void loop() {
    Serial.println(RA_M.getAverage())
    RA_M.addValue(4);
    RA_M.addValue(4);
    RA_M.addValue(2);
    RA_M.addValue(2);
    Serial.println(RA_M.getAverage())
}
```

And the outputs are:

```cpp
0
3
```

To clear the vector to it's default value use the clear() fucntion.


