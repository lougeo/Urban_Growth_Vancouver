Louis George

**<span class="underline">Urban Growth in the Vancouver Metropolitan
Area from 1991 to 2018</span>**

**<span class="underline">INTRO</span>**

In this project I am seeking to find the amount of land use change,
specifically urban growth, in the Vancouver metropolitan area between
the years 1991 and 2018. I will be using data from the USGS portal for
satellite imagery, namely an image from the Global Land Survey database
(taken with the Landsat 5 sensors) for my 1991 reference, and an image
from the Landsat 8 sensors for my 2018 reference. I will be manipulating
and analysing these images in IDRISI’s Terrset program.

I grew up in South Delta which is located south of the larger urban
centers, right near the Canadian/American border. This is an area with a
lot of farmland, and it has indeed managed to keep a significant portion
of this land from being paved over for new malls (although not all of
it). As explained by Burchfield et al.: “Metro Vancouver had a head
start on growth management relative to the Greater Toronto and Hamilton
Area. Starting in the 1970s, British Columbia put in place strong
protections for agricultural land with its Agricultural Land Reserve.
But it is a consistent and long-standing approach to urban containment,
to prevent growth from spilling into the countryside, that has produced
results, including a reduction in the amount of land used for urban
expansion and a greater diversity of housing stock. In recent years,
Metro Vancouver has taken a more strategic approach to growth
management, directing intensification to frequent transit corridors and
urban centres.” (Burchfield, 8). From this kind of management we would
hope to see only a modest increase in built-up area over the 27 years
which I will look at in my study. Despite this, due to population growth
during this time, I expect to see a growth of urban land use, and a
decrease in farmland/vegetation, as well as forested areas. A
distinction which is made in both Burchfield, and Darriau’s studies is
the distinction between intensification – increasing the capacity of
existing urban areas – and greenfield development – creating new urban
areas from other land uses, also known as urban sprawl. I will not be
taking into account any population data in my study, and will therefore
be focusing on urban sprawl.

**<span class="underline">METHODOLOGY</span>**

The study area which I will be looking at is, as previously stated. The
metropolitan area of Vancouver, as shown here in a natural composition:

![first map](https://github.com/lougeo/Urban_Growth_Vancouver/blob/master/LS8_NATCOMP.BMP)

On the following page is a flowchart which depicts the steps I took in
completing this project. I will now elaborate on certain decisions which
were made in this process:

  - Not all of the bands were used from either sensor. From the Landsat
    5 sensor I used bands: 1, 2, 3, 4, 5, 7.From the Landsat 8 sensor I
    used the bands: 1, 2, 3, 4, 5, 6. The other bands which were
    available weren’t used because of several reasons including: they
    were thermal images, the radiometric correction did not turn out
    well.

  - I initially clipped my raster images using a vector file of the
    Vancouver census area. This looked nice, however I quickly ran into
    several problems with this method. The main problem was that Terrset
    does not recognize No Data values, and therefore all of the excess
    area outside of the clipped image took on 0 values which interfered
    with further processes. Other problems included that the vector file
    clipped the ocean out, however it included rivers and lakes, and
    therefore it wouldn’t have removed the need to classify water. My
    solution to this problem was to clip the images using the WINDOW
    tool in Terrset. This method didn’t give me an exact, or official,
    area to work with, however for the limits of this project it worked
    well enough.

  - I decided to settle on 4 categories for my classification, namely:
    water, farmland/vegetation, forest, and urban. I was initially going
    to focus on both urban growth, and farmland lost, however I came to
    realize that I would have also had to add another category for
    random vegetation, because there are obviously areas which are
    green, but are not farmland, but which surely have a similar
    spectral signature to farmland; such as fields, parks, etc… Because
    of this I decided to include vegetation with farmland, and focus on
    urban growth.

  - I decided to use the Minimum Distance classification algorithm
    simply because it produced the most coherent maps by a long shot. I
    did go back and add and remove polygons from my training set,
    however I would have had to spend a LOT more time to satisfactorily
    differentiate the spectral signatures to a point where the other
    classification algorithms would have produced a satisfactory map.

  - For my accuracy assessment, at the advice of Angela Kross, decided
    to have an order of magnitude more points per category than the
    total number of categories. In my case this resulted in a 40 points
    per category, for a total of 160 points.

  - I had to calculate both the error of commission, and the error of
    omission in a separate spreadsheet. This was due to the fact that
    when converting from vector point data to raster, the background
    takes on a 0 value, which is then recognized in the ERRMAT tool as a
    value to include.

  - For map \#4 I reclassed the map in order to change the -1 value to a
    value of 2 in order to be able to have the 0 value be black.

![Flow Chart](https://github.com/lougeo/Urban_Growth_Vancouver/blob/master/GEOG%20465%20PROJECT%20FLOW.jpg)

**<span class="underline">RESULTS/DISCUSSION</span>**

![second map](https://github.com/lougeo/Urban_Growth_Vancouver/blob/master/GLS_MINDISTRAW.BMP)Map \#1

| **Error Matrix Analysis: Landsat 5 - 1991** |             |             |             |             |           |             |
| ------------------------------------------- | ----------- | ----------- | ----------- | ----------- | --------- | ----------- |
|                                             | **1**       | **2**       | **3**       | **4**       | **Total** | **ErrorC**  |
| **1**                                       | 41          | 0           | 0           | 0           | **41**    | **0.00000** |
| **2**                                       | 1           | 21          | 2           | 6           | **30**    | **0.30000** |
| **3**                                       | 1           | 9           | 22          | 2           | **34**    | **0.35294** |
| **4**                                       | 2           | 5           | 8           | 39          | **54**    | **0.27778** |
| **Total**                                   | **45**      | **35**      | **32**      | **47**      | **159**   |             |
| **Error0**                                  | **0.08889** | **0.40000** | **0.31250** | **0.17021** |           |             |
| **Overall accuracy (%)**                    |             |             |             |             |           |             |
| **77.36**                                   |             |             |             |             |           |             |

![third map](https://github.com/lougeo/Urban_Growth_Vancouver/blob/master/LS8_MINDISTRAW.BMP)Map \#2

| **Error Matrix Analysis: Landsat 8 - 2018** |             |             |             |             |           |             |
| ------------------------------------------- | ----------- | ----------- | ----------- | ----------- | --------- | ----------- |
|                                             | **1**       | **2**       | **3**       | **4**       | **Total** | **ErrorC**  |
| **1**                                       | 41          | 0           | 0           | 1           | **42**    | **0.02381** |
| **2**                                       | 1           | 14          | 1           | 5           | **21**    | **0.33333** |
| **3**                                       | 1           | 9           | 18          | 2           | **30**    | **0.40000** |
| **4**                                       | 0           | 7           | 8           | 52          | **67**    | **0.22388** |
| **Total**                                   | 43          | 30          | 27          | 60          | **160**   |             |
| **Error0**                                  | **0.04651** | **0.53333** | **0.33333** | **0.13333** |           |             |
| **Overall Accuracy (%)**                    |             |             |             |             |           |             |
| **78.13**                                   |             |             |             |             |           |             |

![fourth map](https://github.com/lougeo/Urban_Growth_Vancouver/blob/master/URBAN_GROWTH_OVERLAP.BMP)Map \#3

![fifth map](https://github.com/lougeo/Urban_Growth_Vancouver/blob/master/URBAN_GROWTH.BMP)Map \#4

| Urban Growth    |                  |
| --------------- | ---------------- |
| Category        | Square Kilometer |
| Urban Growth    | **251.0856**     |
| Urban Reduction | 76.2381          |

Graph \#1

<span class="chart">\[CHART\]</span>

As is shown in map \#1, map \#2, and perhaps more easily comparable in
graph \#1, the classification did indeed (thankfully) show the
following:

  - An increase in urban area.

  - A decrease in both farmland/vegetation, and forested areas.

  - Only small fluctuation in water area.

Overall these are indeed the trends which I hoped to achieve in this
project. As is shown in the accuracy assessments under maps \#1, and
\#2, I achieved an underwhelming 77.36 %, and 78.13 % for my overall
accuracy respectively. Although these are sub-par results, and even in
the context of assignment 2 would have had to been redone, I do not have
the luxury of time and will have to be ok with these figures.

In maps \#3, and \#4, I isolate the urban growth category and compare
the 1991, and 2018 results directly. As described in the methods, I do
this first by adding the isolated maps to each other using OVERLAY. I
realized, however, that this could be giving me some misleading
information because there are areas which are categorized as urban in
1991, and then as something else in 2018. The result of this would make
it seem as though there was more urban growth than is actually suggested
by the data. This is because:

  - 0 value represents no change.

  - 1 value represents urban growth but could be achieved in two ways,
    one intended, the other unintended:
    
      - Intended: 2018 value = 1, 1991 value = 0.
    
      - Unintended: 2018 value = 0, 1991 value = 1.

  - 2 value represents the urban areas which remained urban.

To work around this, the map \#4 was created by subtracting the 1991 map
from the 2018 map using OVERLAY. The values which were obtained from
this were 1, 0, and -1, where:

  - \-1 represents urban reduction from a 2018 value = 0, 1991 value =
    1.

  - 0 value represents no change from either 0, or 1 values for both
    years.

  - 1 represents urban growth from a 2018 value = 1, 1991 value = 0.

This difference represents one of two methods of obtaining the amount of
urban growth:

1.  By calculating the area of the urban growth category from map \#4,
    from which we obtain a value of **251.0856 km2**. This method
    accounts for the difference between the two years.

2.  By comparing the differences of total urban growth between the two
    years (obtained from graph \#1’s data): 727.0812 – 552.2337 =
    **174.8475 km2**.

In what appears to be a graduate level project, Gabriel Townsend Darriau
calculated that the built-up area in Vancouver increased from 798 km2 in
1991 to 992 km2 in 2011. This is a difference of 194 km2, which is
relatively similar to my values. This makes me happy because it means
that my results were not absurd. To be completely honest I am not sure
why method \#2 is less than method \#1, I was expecting the opposite.
One thing worth mentioning is that it is apparent that both the landsat
5 (1991), and landsat 8 (2018) map classifications had a hard time
(although it is more evident in landsat 5) at differentiating between
farmland, and urban areas. This is evident from the shape of some of the
clusters of classified areas which are outside of the urban centers, and
are clearly plots of farmland.

**<span class="underline">CONCLUSION</span>**

As was the common sense hypothesis in this case, according to this
classification project, urban growth has indeed occurred over the past
30 odd years in Vancouver. Although my analysis confirmed this result, I
do not have very much confidence in the accuracy and precision of the
results. This is because the overall accuracy was too low (just below 80
% for both maps, and this was with an accuracy assessment which could
have been significantly more rigorous), and I doubt that this would
stand up to statistical scrutiny. As previously mentioned, there were
certain problems which plagued the classification algorithms. The most
common were: confusion between farmland and urban areas, as well as
confusion between water and forested areas. Both of these errors occur
due to the two opposite extremes in the spectral signatures; the
farmland/urban confusion was due to similarly high reflectance, and the
water/forest confusion was due to similarly low reflectance values.

In this project I chose to stick with supervised classification
algorithms because of time constraints; after briefly attempting a few
unsupervised algorithms, and investigating the spectral signatures of
the images, it was apparent that quite a lot of time would be required
to tweak the settings in order to obtain a satisfactory result. It would
be a good idea to pursue unsupervised classification if there was more
time available.

The best way to improve the results of this project would be to go back
and continue refining the classification training set. As such, the main
source of error was undoubtedly the human error involved in selecting
the training sets. Another potential source of error was the human error
involved in verifying the point data used in the accuracy assessment.
The ideal method to reduce this error would be to either go out into the
real world and verify the points, or at least verify them through up to
date aerial photography (or some image with better resolution than that
of the Landsat sensors).

**<span class="underline">DATA SOURCE</span>**

<https://glovis.usgs.gov/> (Accessed 2019)

**<span class="underline">REFERENCES</span>**

Darriau, G, T. (2017) *Measuring Urban Sprawl in Vancouver from 1971 to
2011.* Concordia Geography Labs.

Burchfield, M., & Kramer, A. (2015). *Growing Pains: Understanding the
New Reality of Population and Dwelling Patterns in the Toronto and
Vancouver Regions*. Neptis Foundation.
