Signal and background trees for smeared events, in .ROOT:
https://cernbox.cern.ch/s/LyouwrKUNV2oR03
https://cernbox.cern.ch/s/HcC6fFkBc0mm5RI

Below you can find some code, just as an example, to describe how the .ROOT tree data can be used


The histograms can be drawn with commands similar to the ones here:
```
  sig_tree.Draw("mass>>sig_mass", f"57 * 363 / 5e6 * weight * (score > {thr}) * (pt < 105.66*2e-3/sqrt(10)) ")
  bkg_tree.Draw("mass>>bkg_mass", f"2 * 186e3 * 363 / 42179e3 * weight * (score > {thr}) * (pt < 105.66*2e-3/sqrt(10)) ")
```

57/186e3 are the cross-sections in femtobarns, 363 is the luni, 5e6/42179e3 is the number of generated events
The background is multiplied by 2 because the 42179e3 were split in two to train the classifier and only the test events are used here
