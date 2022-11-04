## TIME
16 hours for day and 8 hours for night.  
Calculation will be done on both day and night.

## UNIT
Metric system used

# DEFINITIONS

# WOODS    
Trees between the road/rail segment and the receiver which
extend at least 5 metres above the line-of-sight.  The trees
must be dense so that there is no visual path  between the
segment and the receiver.  If the above  conditions are met,
an adjustment of 5 dBA may be applied  to each 30 metre
depth up to a maximum adjustment of 10 dBA.

# HOUSES   
Rows of houses between the road/rail segment and the
receiver which may provide noise attenuation.  For the first
row, an adjustment of up to 10 dB may be applied, dependent
on the density of the first row of houses.  Allowable house
density is between 20 % and 95 %.  An additional adjustment
of 1.5 dB is applied for each successive row. Rows of houses
occupying greater than 95 % density should be treated as a
solid acoustic barrier.

# SOURCES:  ROAD
Road traffic is separated into three vehicle categories:  automobiles, medium
trucks and heavy trucks.   

The source of noise is assumed be produced by the
combination of the three categories; the height of the source above the road
is proportional to the percentage of heavy trucks.


2 road segments: IF THE JUNCTION DOES NOT MODIFY THE TRAFFIC VOLUMES FOR EITHER ROAD.
4 road segments: IF THE TRAFFIC VOLUMES ON EITHER SIDE OF THE JUNCTION ARE DIFFERENT.


# SOURCE (SubLeq1 + SubLeq2 + SubLeq3) = "SOURCE" Segment Leq

   "SOURCE" may be ROAD, RT/CUSTOM, LOCOMOTIVE, WHEEL-RAIL or WHISTLE

   Angle1:  Leftmost angle defining the segment or subsegment (e.g. barrier)  
   Angle2:  Rightmost angle defining the segment or barrier  
   Alpha:   Value of the ground absorption coefficient  
   RefLeq:  Reference sound level (at 15 m)  
   D.Adj:   Distance adjustment  
   F.Adj:   Finite segment adjustment  
   W.Adj:   Woods adjustment  
   H.Adj:   Row of houses adjustment  
   B.Adj:   Barrier adjustment  
   SubLeq:  Leq for the segment or subsegment defined by angles 1 and 2  
   Source Height:   Ranges between 0.5 and 2.4 m.  (Function of Heavy Truck %)  
   Segment Leq:     Leq for the current (selected) road segment  
   Total Leq Road:  Total road traffic Leq for all road segments     
   Total Leq Rail:  Total rail traffic Leq for all rail segments  
   Total Leq Gen :  Total Leq from Rapid Transit or Custom sources, all segm  
   Total Leq: Combined Leq of road and rail traffic for all segments  

# REPORT
Normal 
Detail results for every segment.


# Output

*Name*: Name of the text (output) file.
*2nd Receiver*: User may define a height of another (2nd) receiver by means of an offset with respect to the original receiver height defined in the input data.  The same offset is applied to receivers defined in the data with differing heights, as in 
            
Day/Night situations or for receivers in different segments. Note that if 2nd receiver is defined, barrier table cannot be generated and is automatically set to OFF.


## Srce Rec Dist Night
 The separation  distance between the noise source ( i.e. the centre line of the traffic lane) and the receiver (the observer), defined specifically for night-time period. 
    
This night-time distance may only be specified when all the angles are infinite, i.e. from -90 to 90 degrees.  When any of the angles are finite, segment angles or barrier angles, or when whistle angle is specified, this field does not appear.

# Receiver Height Night (r) 
  Receiver height for the night-time receiver. May differ from the day-time receiver height. Default is 4.5 m.

# No of Rows of Houses Night 
Number of rows of houses between the night-time receiver and the road. May differ from the day- time case. Default is 0.


## Calculate Road Volume

This function calculates the automobile, medium and heavy truck volumes from the average daily road traffic and truck percentage information.

The future projected traffic volumes are also calculated based on the expected annual increase and the number of years.  The user must also specify the percentage split of road traffic volume occurring during day-time and night-time.

SOURCES: RAPID TRANSIT (RT) (TORONTO TRANSIT COMMISSION (TTC)) / CUSTOM

One RT/Custom vehicle category may be defined per segment.  The RT vehicle categories are: buses, street cars (ALRV & CLRV), subways and SRT vehicles.
If the traffic contains more than vehicle catagory, CLRV and ALRV for example,
multiple segments must be defined.

The vehicle categories are defined by pressing CTRL_PGUP or 

The RT vehicles have their sound emission levels and source heights (0.5 m) pre-defined; these values must be user entered for the Custom vehicles.

The sound emession level is the maximum pass-by sound level (SLOW), measured at a distance of 15 m from the center of the vehicle path.

The source height represents the height of the dominant source above ground level.



  ### Source Height
Equals to 0.5 m for Rapid Transit vehicles. User input value for Custom vehicles.

  ### Segment Leq:     Leq for the current (selected) RT/Custom segment

   Total Leq Road:  Total road traffic Leq for all road segments
   Total Leq Rail:  Total rail traffic Leq for all rail segments
   Total Leq Gen :  Total Leq from RT or Custom sources, all segm

   Total Leq:       Combined Leq of road and rail traffic for all segments


### CUSTOM 
   If the Custom category is selected, the noise emission level and
   the source height must also be input through Menu, Source and Segment.

     Bus:          TTC bus
     CLRV:         TTC street car - Canadian Light Rail Vehicle
     ALRV:         TTC street car - Articulated Light Rail Vehicle
     6-car Subway: TTC subway train consisting of 6 cars
     4-car SRT:    TTC Scarborough Rapid Transit train, 4 cars
     Custom:       Any vehicle defined by the user; enter source height
                   and sound emission level (SPL @ 15 m)
                   
 
