# hp-41_DSTAT.ROM
Comprehensive statistical analysis of data sets on the HP-41 calculator

## HP-41: STATistical analysis galore

This ROM serves two programs; "DATA" for statistical data entry and management of both single and double variables, and "STAT" that does curve fitting and statistical analysis of single and double variable data sets. The "STAT" program has taken its main part from William Kolb’s book "Curve Fitting for Programmable Calculators" with the added basic statistcs, momentums, kurtosis and skewness of data. You will find Kolb’s excellent book over at hp-41.org.

### DATA

This program simplifies the entry and handling of data sets, storing and retrieving data sets from extended memory (XM)

Enter the file name of the data set in Alpha and XEQ "DATA". If no file name is given or the file name given does not exist, you will have to XEQ C to create a new data set. A file name that includes the numbers 1 or 2 indicates whether the data set is for single values of Y or paired X & Y values and flag 1 or 2 will be set accordingly.

Upon execution, the program shows labels A-E and labels a-e as successive prompts:

**__+ 1:2 C:S >s V__**

**__- FX XG FM P__**

The meaning of each label:

Label: (prompt)    | Description
-------------------|------------
LBL A: + | Adds data (single [X] or double [X&Y] depending on whether flag 1 or 2 is set) to XM file
LBL B: 1:2 | Toggle single or double data entry (sets flag 1 or 2 respectively)
LBL C: C:S | Makes file name in Alpha the current data set file or creates the file if file name is not found. Creates the file as a single or double variable set depending on whether flag 1 or 2 is set (remember to ensure the correct flag is set first – by using LBL B). In creating a data set, you must supply the first variable(s) as you would with LBL A to kick off the data set
LBL D: >Σ | Calls the MCF+ routine in the “STAT” program (see below) and thereby processes the data set created for digestion by the “STAT” program, then jumps directly to the “STAT” program (see below). It start with the data point number in X and ends with the data point number in Y. So, if you want to analyze the points 5->16 in a data set, just do “16 ENTER 5” before pressing D. If you want to process the whole data set, ensure both register X and Y contains 0.
LBL E: V | View the data set, with the Y-value in X and the X-value in Y. If flag 1 is set, the X-value shown is incremented from zero and upwards.
LBL a: – | Remove the last entered data (like s-)
LBL b: FX | Toggle flag 0. If flag 0 is set, it freezes the data set so that it becomes of fixed size. Newly entered data point(s) will then move the earliest data point(s) out of the data set. This is usefull for analysing moving averages, a set time period (such as quarterly or 12-months data), etc.
LBL c: XG | XM Get; Get file (name in Alpha) from extended memory. After retreiving the file, new data points can be added (LBL A) to enlarge the data set (or if flag 0 is set, keep the size but move the earliest data out of the file)
LBL d: FM | Go to the FILEMAN program
LBL e: P | Shows Properties of the data set and Prints the data set on the attached printer as a graph. First it will show the Min/Max/median of Y and of X before it asks whether you want to commence printing. Press R/S to thus commence.
LBL I | Shortcut to printing the data set as a graph. When using this shortcut, the Y-MIN and Y-MAX has not been calculated as with LBL e, so you have to enter it manually (Y-MIN [ENTER] Y-MAX)
LBL J | Back to showing the manu for labels A-E and a-e

### STAT

This program performs basic statistical analysis, moments, kurtosis, skewness and curve fitting (the 19 different curve types in Kolb’s book).

Upon execution, the program shows labels A-E and labels a-e as successive prompts:

**__+ >I BF Y BΣ__**

**__- .- DATA X \*__**

The meaning of each label:

Label: (prompt)    | Description
-------------------|------------
LBL A: + | Add one data point (like s+). This is for manual input of data points. Use the “DATA” program above if you want to work with data sets and have the ability to save and restore the sets to XM
LBL B: >I | Enter the curve index (1-19) from Kolb’s book and get the function and its constants and correlation coefficient displayed. This will now be the selected curve type for showing X or Y (LBL D or d)
LBL C: BF | Calculate the best curve fit and show the formula for that function along with its constants and correlation coefficient. This will now be the selected curve type for showing X or Y (LBL D or d)
LBL D: Y | Calculate Y from the X given in the X register for the selected curve type
LBL E: BΣ | Show the basic statistical data for the entered data set
LBL a: – | Remove last data point entered (like s-)
LBL b: .- |
LBL c: DATA | Goto the “DATA” program (see above)
LBL d: X | Calculate X from the Y given in the X register for the selected curve type
LBL e: * | Back to the main menu (prompts showing labels A-E and a-e

### RG

Included in the ROM is a random number generator. "RG" returns a random number between 0 and 1. This Random Number Generator  uses TIME as input, rendering the numbers generated “more random” than the usual HP-41 solutions that keeps a seed stored for the next value generated. If there is no Time module, RG instead takes the value in X and Y as seeds.
