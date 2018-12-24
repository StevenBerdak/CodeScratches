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

## <b>boolean filterMapMarkersByRegion(List<DotEvent> baseEventsList, double eastLngBound, double westLngBound, double lngPoint)</b>

Determines if a given longitude point is within longitude bounds in a view which contains lat and lng bounds
``` 
    static List<DotEvent> dotEventsByRegion(List<DotEvent> baseEventsList,
                                            double northLatBound,
                                            double eastLngBound,
                                            double southLatBound,
                                            double westLngBound) {
        northLatBound = clampDouble(GOOGLE_MAPS_MAX_LAT_S, GOOGLE_MAPS_MAX_LAT_N, northLatBound);
        southLatBound = clampDouble(GOOGLE_MAPS_MAX_LAT_S, GOOGLE_MAPS_MAX_LAT_N, southLatBound);
        eastLatBound = clampDouble(GOOGLE_MAPS_MAX_LNG_W, GOOGLE_MAPS_MAX_LNG_E, eastLatBound);
        westLatBound = clampDouble(GOOGLE_MAPS_MAX_LNG_W, GOOGLE_MAPS_MAX_LNG_E, westLatBound);

        boolean acrossAntipodal = westLngBound > eastLngBound;

        List<DotEvent> result = new ArrayList<>();

        for (DotEvent event : baseEventsList) {
            double pointLat = event.latitude;
            double pointLng = event.longitude;

            if (!acrossAntipodal) {
                if (pointLng <= eastLngBound && pointLng >= westLngBound &&
                        pointLat <= northLatBound && pointLat >= southLatBound) {
                    //Range is not located across the antipodal meridian, check if in range
                    result.add(event);
                }
            } else {
                //Range is located across the antipodal meridian, check if in range
                if (pointLng >= westLngBound || pointLng <= eastLngBound &&
                        pointLat <= northLatBound && pointLat >= southLatBound) {
                    result.add(event);
                }
            }
        }

        return result;
    }
```

## <b>Css inner box shadows</b>

Simply adds an inner box shadow to a css container

/* offset-x | offset-y | blur-radius | spread-radius | color */

```
     .top-box
     {
         box-shadow: inset 0 7px 9px -7px rgba(0, 0, 0, 0.4);
     }
     .left-box
     {
         box-shadow: inset 7px 0 9px -7px rgba(0, 0, 0, 0.4);
     }
     .right-box
     {
         box-shadow: inset -7px 0 9px -7px rgba(0, 0, 0, 0.4);
     }
     .bottom-box
     {
         box-shadow: inset 0 -7px 9px -7px rgba(0, 0, 0, 0.4);
     }
     
     .top-box-minimal
     {
         box-shadow: inset 0 4px 4px rgba(0, 0, 0, 0.25);
     }
```
