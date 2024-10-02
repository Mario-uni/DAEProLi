# DAEProLi
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Mario-uni/DAIProLi/blob/main/DAIProLi_6_esp.ipynb)

## Overview
DAIProLi is a python script that allows you to analyze the data generated by differential spectroscopy experiments.

## Usage
This software is created in Google Colab. To access it, click on the Google Colab badge above or on this [link](https://colab.research.google.com/github/Mario-uni/DAIProLi/blob/main/DAIProLi_6_esp.ipynb).

**Step 1**: Check the format of the data you have, you need to export your spreadsheet into a csv file. The way the data is saved must be the same as in the following example:
**Example 1**
| Wavelength nm.    | Baseline |  2 | 4 | 6 | ... |
| -------- | ------- | ------- | ------- | ------- | ------- |
| 300    | -0.0002    | 0.0004     | 0.0031     | 0.0034     | ...   |
| 300.5  | -0.0001    | 0.0004     | 0.0029     | 0.0034     | ...   |
| 301    | -0.0002    | 0.0002     | 0.0027     | 0.0032     | ...   |
| ...    | ...   | ...    | ...   | ...   | ..   |

**Step 2**: Load the libraries and functions *(Librerias y funciones)*. This step only needs to be performed once, regardless of the number of datasets processed.

**Step 3**: Run the next cell *(Subir archivo y formato csv)* and do not change the parameters. A message will appear below it asking you to select the file to be uploaded.

**Step 4**: Run *PreprocesaAbsorbance*, in this cell the difference between minimum and maximum in each spectra will be performed.

**Step 5**: In this cell *(Gráfico espectros)* you will be able to plot the spectra recorded for each condition in 2D and 3D. You have the option to adjust all spectra so that their absorbance is zero at a given target wavelength.

**Step 6**: Here, in *Modelo*, the model that may explain the experimental data is written

**Step 7**: In this cell *(Gráfico ΔAbsorbancia vs Volumen (µL))* the data generated from *PreprocesaAbsorbance* will be plotted.

**Step 8**: The **Parámetros** cell is very important. Here you will write the parameters needed by the model and select whether they are fixed or not. If the parameter is fixed, the **procesa** function (responsible for the fitting) will not optimize those values. **Warning:** if the values inputted for the parameters differ greatly from reality even if they are marked as not fixed the fitting process might have worse results or even fail. A good initial estimation, will provide a better fitting.

**Step 9**: Run the *Procesa* cell which will perform the fitting via the least squares method.

**Step 10**: Here *(Gráfico Δ Absorbancia vs Volumen (µL) con el ajuste del modelo)* you can plot the the data genertaed from *PreprocesaAbsorbance* (experimental data) and the values obtained using the model and the optimized parameters from **procesa**.

**Step 11**: Lastly, this cell saves and export all the data inputted and generated. The datasets are saved in csv format and the plots are saved in html and png. All of this items are downloaded in a zip which you can name (but it will always have the date and hour of when the cells was run as suffix).

## Troubleshooting

### Case 1: CSV formatting
The program was created to handle csv whose numbers have points for decimal separators and commas for thousands separator. Other formats will not be read properly by the program. 
The most common alternative format is to have commas as decimal separators and points as thousands separators. In this particular case there are several solutions depending on the spreadsheet software used:

### Excel
In the latest versions of this software you can use the solution depicted in the following [YouTube video](https://www.youtube.com/watch?v=TC_guUz64i8). Once you have opened the dataset:
1. Click on **File**.
2. Then, go to **Options**.
3. In the new window that appears, click on **Advanced**.
4. Once there look for the Use system separator and modify the decimal and thousands separator accordingly ("," and "."  respectively).

Beware this can only be done in the Desktop version of Excel, the online version of Excel lacks this personalization and for the moment lacks a solution.


### Google Spreadsheet
You only need a Google account to access it, which you also need to run the program, so everyone can have access to this software (and a relativey good Internet connection). Moreover, the solution is a bit more straightforward.  Once you have opened the dataset:
1. Click on **File**.
2. Then, click on **Settings**.
3. In the new window set the **Regional settings** to English (EE.UU.).
The drawback is that in this case all formats will change to those of the United States (e.g. dates, ...). However, it can be easily changed any time.

### LibreOffice Calc
LibreOffice Calc is part of the LibreOffice environment and is free of charge. Once you have opened the dataset:
1. Click on **Tools**.
2. Then, click on **Options**.
3. In the new window that appears, click **Languages and regions**, and then on **General**.
4. Once there set **Regional configuration** to English (EE.UU.).
This has the same drawback that Google Spreadsheet but can be personalized a little bit further.


