# CodeScratches
Random code that I could not let go of so it goes here! :)


## <b>long[] arrayOfNowTimeDifference(long subtrahend)</b>

Calculates the difference between a time value and the current time retrieved with `System.currentTimeMillis()`
```
     /**
     * Returns an array that contains the difference between the current time and the provided time.
     * @param subtrahend The time to subtract frm the current time.
     * @return An array containing 3 values that represent days, minutes and hours respectively.
     */
    public static long[] arrayOfNowTimeDifference(long subtrahend) {
        long currentTime = System.currentTimeMillis();

        long difference = currentTime - subtrahend;

        long minutes = (difference / (1000 * 60)) % 60;

        long hours = (difference / (1000 * 60 * 60)) % 60;

        long days = (difference / (1000 * 60 * 60 * 24));

        return new long[]{days, hours, minutes};
    }
```

## <b>boolean isPointWithinLngRange(double eastLngBound, double westLngBound, double lngPoint)</b>

Determines if a given longitude point is within longitude bounds
    
    
   !!!! edit: needs fixed, not circular!!!!
```
    let min = -180.00;
    let max = 180.00;

    let e = eastLngBound;
    let w = westLngBound;

    let x = lngPoint;

    let range = e - w;

    x = x + 180 + range;
    e = e + 180 + range;
    w = w + 180 + range;

    if (x <= e && x >= w) return true;
```
