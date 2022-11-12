# LS_Series_Gaps_Jupyter

This routine analyses the effect of data gaps on the spectral output of the Lomb-Scargle (LS) algorithm applied to a sythetic harmonic time-series.
The gaps may be padded with zeros or simple jumps from the end of one data sequence to the beginning of the next.
The gaps may also be cut-off abruptly (using an inverse top-hat window function) or tapered through the used of a Tukey filter.

The dataset is simple: 1000 points with a 0.01 day cadence, resulting in a 10-day time-series. It comprises of a superposition of four in-phase sinusoidal signals with frequencies of 10, 20, 30 and 40 cycles per day (c/d), respectively, all with unit amplitudes.

----

![50pcTimeSeries](https://user-images.githubusercontent.com/81772405/201449555-810eea74-2ee6-44e9-b7a1-f0d51a7fbdc9.jpg)

**Figure 1:** Synthetic 10-day time-series at 0.01-day candence (*blue*). Modulating this signal with an inverse top-hat window function (*green dashes*) creates an abrupt gap within the center of the time-series. The entry and exit points of the gap may be tapered to and from zero by modulating the signal with a new window-function (red), where the inverse top-hat is tapered with a Tukey filter of a user-defined size (101 elements in this case).

----

A number of time-series are created with data gaps between 0% to 99% of the full data range (i.e. 0 to 990 points in steps of 10 points), all centralized with respect to the time-series. Among other options, characteristics of the time-series may be controlled using a number of switches:
- abrupt onset of the gap using an inverse top-hat function, or taper to zero with a Tukey filter. For the latter, the taper length is adjustable,
- retain zeros within the gap to pad the dataset, or remove to produce a data-jump. Both options have different effects on the characteristics of the LS signals,
- the normalization of LS amplitudes to better relate certain results,
- add noise to the time-series,
- save the plots to file.

With zero gap, the Lomb-Scargle spectrum displays all four signals with unit amplitude at their respective frequencies. Note that no artifacts exist around the signal peaks, the peak shapes are a result of the 0.1 c/d frequency resolution.

----

<img src="https://user-images.githubusercontent.com/81772405/201450431-fd3dfa3e-6816-4735-8c62-a61f5aaba260.jpg" width="390" /><img src="https://user-images.githubusercontent.com/81772405/201450434-43ca9895-dece-4455-be6a-0607b214f215.jpg" width="400" />

**Figure 2:** Lomb-Scargle frequency spectrum of a time-series with no gap and no noise. (*Left*) The full spectrum showing the four components of the time series. (*Right*) The 10 c/d, unit-amplitude peak shows no artifacts. It drops immediately to zero at 0.1 c/d either side of the peak, relating to the frequency resolution of the spectrum.

----

While various combinations of switches maybe applied to the analysis with the output being produced for any data-gap, in what follows, for the purposes of an example, Lomb-Scargle amplitudes will be produced from a noiseless time-series with a data-gap of 50% (see Figure 1) that is:

<ol type="a">
  <li>unpadded, abruptly cut-off gap (inverse top-hat),</li>
  <li>padded, abruptly cut-off gap (inverse top-hat),</li>
  <li>unpadded, tapered gap (Tukey, 51 elements for each taper),</li>
  <li>padded, tapered gap (Tukey, 51 elements for each taper).</li>
</ol>

For simplification the LS amplitudes around the first peak of 10 c/d (Figure 2, *left*) will be displayed. Figure 3 illustrates these examples in four plots. Compared with the non-gapped time-series (Figure 2, *right*), the four plots show variations in amplitudes at and around the peak.

----

<img src="https://user-images.githubusercontent.com/81772405/201485322-32cb6bb4-54f4-4695-9442-487f61794dd6.jpg" width="390" /><img src="https://user-images.githubusercontent.com/81772405/201485336-8417517a-3c95-47d0-b129-784ef04ab864.jpg" width="390" />
<img src="https://user-images.githubusercontent.com/81772405/201485363-6dda6974-2bff-4952-8227-496569bb60a1.jpg" width="390" /><img src="https://user-images.githubusercontent.com/81772405/201485371-026b14d7-e42f-4c70-83d0-880c5b15dda8.jpg" width="390" />

**Figure 3:** Plots of the 10 c/d peak for a time-series with a centralized gap extent of 50% of the time-range for the (a)-(d) examples described in the text.

----

Figure 3, plot **(a)** shows a peak with the correct unit-amplitude as before, but with spectral leakage either side of the peak, which are artifacts of the window-function. 

Plot **(b)** exhibits the same spectral leakage artifacts, but with a peak that is reduced in amplitude. This is because the LS algorithm now sees zero power within the gap that brings down the peak normalized-amplitude.

The peak of plot **(c)** has a slightly lower amplitude than that of plot (a). While the gap is not considered by the LS algorithm, the extent of the Tukey filter tapering attenuates the region to zero which is seen by the LS algorithm, reflected in the slightly lower amplitude. It is worth considering what relationship, if any, the peak amplitude has with the taper length. The notable spectral leakage seen in plots (a) and (b) is somewhat suppressed by the Tukey filter, due to the smoother transition of the window function, and is one of the key reasons for its use with time-series data.

Finally, plot **(d)** combines the attributes of all those seen prior. The peak amplitude is noticeably lower than plots (a) and (c) due to the inclusion of the zeros in the data gap, but also slightly lower than that of plot (b) due to the inclusion of the taper. Similar to plot (c), the spectral leakage around the peak is somewhat suppressed, compared to plots (a) and (b).
