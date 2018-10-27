# CodeScratches
Random code that I could not let go of so it goes here! :)

<b>arrayOfNowTimeDifference(long subtrahend) - Calculates the difference between a time value and the current time retrieved with `System.currentTimeMillis()`</b>
```    /**
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
