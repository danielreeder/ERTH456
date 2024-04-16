**Using Filters and Spectrograms to Identify Anomalies in Canadian Weather Patterns**

Daniel Reeder

Department of Earth Sciences, University of Oregon, Eugene, OR, USA.

Key Points:
In general, precipitation and temperature fluctuate primarily on a yearly and bi-yearly basis
Yearly fluctuations are largely uniform throughout time, while bi-yearly fluctuations vary significantly
Major anomalies in bi-yearly fluctuations show up for both precipitation and temperature in the 1980s and late 1990s















Abstract

This project aims to find the standard fluctuations of temperature and precipitation in   Canada, and use this information to identify anomalies in Canadian weather patterns. This is accomplished by using Fourier transforms, filters, and spectrograms to locate important frequencies and see how they change over time. I will use data containing daily measurements of average temperature and total precipitation in various regions in Canada from 1960 to 2020. By analyzing the amplitude spectra of each region, Edmonton was selected to be the region of focus for this study due to its distinct peak frequencies. Filters were used to isolate the peak frequencies, corresponding to yearly and bi-yearly intervals. Visualizing the filtered data and the amplitude of its frequency throughout time with spectrograms led to the identification of multiple anomalies, specifically in the bi-yearly interval. These anomalies occur in both precipitation and temperature data, around the same time. To confirm the association between the two measures at these frequencies, I plotted the coherence between them. This verified that the correlation between temperature and precipitation was strongest at yearly intervals, with a second, smaller peak at bi-yearly intervals. Further research into this subject would require similar analysis performed on the other regions featured in the dataset in order to determine whether or not these anomalies are common to a larger region or indicative of real changes in the climate.

1 Introduction
	
  Changes in precipitation and temperature themselves have been used as indicators in climate change studies (Reyes-García et al.). The idea behind this project is that looking at changes in how precipitation and temperature are changing could potentially help analyze climate change as a whole within a given area. Identifying times when there have been anomalies in one or both of these measures provides an indication of periods that warrant further investigation to determine what factors caused the anomaly. Once these factors are identified, they can be used to predict future anomalies.
This project will address the first step of the process described above. Using Canadian temperature and precipitation data, an area of focus will be chosen as the subject of further analysis. I will aim to identify anomalies of two kinds: changes in the prevalence of any of the peak frequencies, and any times at which a non-peak frequency stands out as more important than normal. Signal processing techniques used include the Fast Fourier Transform (FFT), infinite impulse response (IIR) filters, and spectrograms. Ultimately this study focuses only on data gathered in Edmonton, Canada, though a complete investigation into this subject would analyze data from other regions of the country and attempt to establish a pattern of anomalies throughout a larger area.

2 Data
	
  The data used in this study originates from the government of Canada and was compiled for easier use by Anna Turner. The dataset contains daily recordings of average, maximum, and minimum temperature, as well as total precipitation, from 13 different stations around Canada.
Data preprocessing was used to limit the scope of this study to daily average temperature and total precipitation at the Edmonton station. Edmonton was selected as the region to focus on based on a visual analysis of the amplitude spectra of each location, with the goal of selecting the region that had clear peaks in both the temperature and precipitation spectra. Both temperature and precipitation have peaks at frequencies of 1365 and 1182, corresponding to periods of one year and half of a year. 


3 Methods and Results

  This study primarily made use of four signal processing techniques: the Fast Fourier Transform (FFT), infinite impulse response (IIR) filters, spectrograms, and coherence. Spectral analyses of weather data such as this generally make use of the continuous wavelet transform and scalograms, rather than the FFT and spectrograms (Pasero et al.). The FFT was used for this study both because of time constraints, and because I found it to be sufficient for identifying the long-term trends necessary for this project. Additionally, a similar study on weather patterns suggests separating the data by season and analyzing seasonal patterns separately (Anderson, Subbarao). Again, I opted against this because of the objective of capturing long-term trends. Similar methods of detecting anomalies with spectrograms have been used in other fields, such as healthcare (Li, Pierre) and computer science (Joydeep et al.).

3.1 Fast Fourier Transform

  The FFT was used to produce the amplitude spectra of temperature and precipitation for each of the 13 weather stations included in the original dataset. The FFT was calculated using the fft function from scipy.fftpack, and was visualized using SciPy’s fftfreq function to determine the corresponding frequencies. This was first used to gain a broad understanding of the frequencies that commonly show up in the data, and later used to select one station to analyze further. The selected station was Edmonton, due to the clearly identifiable peaks in both spectra, seen in Figure 1. Note that due to the data being sampled at a rate of once per day, it is possible that this analysis misses variation that occurs on a daily or sub-daily interval, particularly the diurnal cycle of precipitation (Berg et al.).

3.2 IIR Filters

  This study utilized IIR filters to isolate the peak frequencies seen in the amplitude spectra. Specifically, 2nd order, bandpass Butterworth filters were used to isolate frequencies corresponding to yearly and bi-yearly fluctuations. The filters were created using the butter function from SciPy’s signal package, and applied using the sosfilt function from the same package. For yearly fluctuations, a filter was used to select frequencies between 2.5x10-3 and 3.0x10-3 cycles per day. For bi-yearly fluctuations, frequencies between 5.3x10-3 and 5.6x10-3 were selected. 

3.3 Spectrograms

  Spectrograms are a method of showing the amplitude of each frequency present in a signal as a function of time. The FFT is calculated for many slices of the data and the information is compiled into a plot with time on the x-axis and frequency on the y-axis, with the strength of each frequency represented by a colormap. In this project, spectrograms were used to identify anomalous times in which certain frequencies have significantly higher or lower strength than normal. 
	The first type of anomaly I tried to identify was frequencies with unexpectedly high strength. Specifically, I looked for higher frequencies that did not show up as peaks on the amplitude spectrum plots. For this purpose, spectrograms of the data were created before filtering, for both temperature and precipitation.


  In Figure 1, the peak of each graph can be clearly seen at a frequency of about 2.7x10-3, or 1365. A much fainter peak shows up in the expected spot at roughly 5.5x10-3, or 1182. In both plots, frequencies higher than either of these peaks seem to fluctuate in strength somewhat randomly, and there are no major anomalies that stand out visually.
The second type of anomaly I attempted to find was changes in the strength of either of the peak frequencies. To look for these anomalies, I created several spectrograms for each peak frequency to allow for easy visual identification. A spectrogram was first created using the filtered data. A second spectrogram was produced which zoomed in on the desired frequency and removed lower strength signals from the spectrogram to increase visual contrast. This was done for both peak frequencies, with both temperature and precipitation data. As in figure 1, these spectrograms are plotted below the corresponding filtered time series. Yearly fluctuations were shown to be mostly uniform throughout the entire timespan, and due to limitations in the number of figures allowed, those spectrograms will not be included. Bi-yearly fluctuations, however, contained multiple significant anomalies.


  Figures 2 and 3 show the spectrograms of both precipitation and temperature data filtered for bi-yearly fluctuations. Both spectrograms have significant fluctuation over time, with two major anomalies standing out on each. These anomalies appear during roughly the same times for both precipitation and temperature, with the first occurring between 1980 and 2000, and the second from 2000 to the mid 2010s.

3.4 Coherence

  The coherence was calculated and plotted after identifying the patterns seen in the spectrograms of both temperature and precipitation. This was done to further verify that temperature and precipitation are correlated at their peak frequencies. A study on temperature and precipitation in Iran found similar peaks in coherence at 6- and 12-month intervals (Neyestani et al.). Another study found that the relationship between temperature and precipitation varies between the summer and winter months (Berg et al.), supporting the coherence seen at bi-yearly periods.

4 Conclusions

  The results of this study have shown that multiple periods of time exist during which the strength of certain peak frequencies dropped in an irregular way. Two such irregularities were identified in both temperature and precipitation data, and analysis of the coherence between these measures confirmed their correlation. This study was, however, conducted with a scope far too small to assign much significance to the findings. Despite this, the fact that these anomalies show up in both sets of data at the same time leads me to believe this process could be repeated with a larger scope, and that further investigation could yield significant results. Possible applications of a larger study on this subject could include prediction of future weather patterns and anomalies, as well as the identification of the underlying factors leading to these anomalies.












References


Anderson, J. V., & Subbarao, K. Spectral Analysis of Ambient Weather Patterns. United States. https://doi.org/10.2172/6946559


Berg, P., J. O. Haerter, P. Thejll, C. Piani, S. Hagemann, and J. H. Christensen (2009), Seasonal characteristics of the relationship between daily precipitation intensity and surface temperature, J. Geophys. Res., 114, D18102, doi:10.1029/2009JD012008.


Joydeep, M., Sumona, M., & Marin, L. (2023, September). Detecting Software Anomalies Using Spectrograms and Convolutional Neural Network. In Proceedings of the 33rd Annual International Conference on Computer Science and Software Engineering (pp. 44-53).


Li, Hongzu, and Pierre Boulanger. 2022. "Structural Anomalies Detection from Electrocardiogram (ECG) with Spectrogram and Handcrafted Features" Sensors 22, no. 7: 2467. https://doi.org/10.3390/s22072467


Neyestani, Abolfazl & Karami, Khalil & Gholami, Siavash. (2022). Exploring the possible linkage between the precipitation and temperature over Iran and their association with the large-scale circulations: Cumulative spectral power and wavelet coherence approaches. Atmospheric Research. 274. 106187. 10.1016/j.atmosres.2022.106187. 


Pasero, E., Montuori, A., & Raimondo, G. (2006). A spectral analysis of meteorological data for weather forecast applications. In Proc. 13th Standing International Road Weather Commission (SIRWEC'06) Conference (Vol. 1, pp. 93-100).


Reyes-García, Victoria et al. “Local indicators of climate change: The potential contribution of local knowledge to climate research.” Wiley interdisciplinary reviews. Climate change vol. 7,1 (2016): 109-124. doi:10.1002/wcc.374


Turner, A (2020). Eighty years of Canadian climate data. [Dataset]. Kaggle. https://www.kaggle.com/datasets/aturner374/eighty-years-of-canadian-climate-data/data







