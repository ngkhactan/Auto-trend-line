#----------------------------------------------------------#
#            Auto Trendline Script           		#
#                                                          #
#                                                          #
#                                                          #
#----------------------------------------------------------#

declare upper;

#################################################
# Defining High, Low and Pivot Points
#################################################
def Hi = high;
def Lo = low;
def P1H = (Hi > Hi[1] or (Hi > Hi[2] and Hi == Hi[1])) and Hi > Hi[-1];
def P1L = (Lo < Lo[1] or (Lo < Lo[2] and Lo == Lo[1])) and Lo < Lo[-1];
def lastBar = HighestAll(if !IsNaN(close) then BarNumber() else 0);
def Piv1h = if P1H[1] then 1 else Piv1h[1] + 1;
def Piv1l = if P1L[1] then 1 else Piv1l[1] + 1;
def PivN1h = fold m = 1 to lastBar with a = Double.NaN while IsNaN(a) do if GetValue(P1H, -m) then -m else Double.NaN;
def PivN1l = fold n = 1 to lastBar with b = Double.NaN while IsNaN(b) do if GetValue(P1L, -n) then -n else Double.NaN;

def prevPivhigh = GetValue(Hi, Piv1h);
def prevPivlow = GetValue(Lo, Piv1l);
def nextPivhigh = GetValue(Hi, PivN1h);
def nextPivlow = GetValue(Lo, PivN1l);
def P2H = Hi > prevPivhigh and Hi > nextPivhigh;
def P2L = Lo < prevPivlow and Lo < nextPivlow;
def p2x2 = P2H and P2L;
def Piv2h = if P2H[1] then 1 else Piv2h[1] + 1;
def Piv2l = if P2L[1] then 1 else Piv2l[1] + 1;
def PivN2h = fold o = 1 to lastBar with c = Double.NaN while IsNaN(c) do if GetValue(P2H, -o) then -o else Double.NaN;
def PivN2l = fold p = 1 to lastBar with d = Double.NaN while IsNaN(d) do if GetValue(P2L, -p) then -p else Double.NaN;
def NextP2H = if PivN2h > PivN2l then 1 else Double.NaN;
def NextP2L = if PivN2l > PivN2h then 1 else Double.NaN;
def NextP2Both = if PivN2h == PivN2l then 1 else Double.NaN;
def PrevP2H = Piv2h < Piv2l;
def PrevP2L = Piv2l < Piv2h;
def PrevP2Both = Piv2h == Piv2l;
def nearLow = if P2L and PrevP2H then Lo else nearLow[1];
def AL0 = if P2L and PrevP2L and Lo > nearLow then 1 else Double.NaN;
def AL1 = if P2L and NextP2L and GetValue(Lo, PivN2l) <= Lo then 1 else Double.NaN;
def AL2 = if p2x2 and PrevP2L and Lo > GetValue(Lo, Piv2l) then 1 else Double.NaN;
def AL3 = if P2L and PrevP2Both and !NextP2H and Lo > GetValue(Lo, Piv2l) then 1 else Double.NaN;
def AL4 = if P2L and PrevP2L and Lo > GetValue(Lo, Piv2l) then 1 else Double.NaN;
def AL5 = if P2L and PrevP2H and NextP2Both and Lo > GetValue(Lo, PivN2l) and GetValue(Hi, PivN2h) < GetValue(Hi, Piv2h) then 1 else Double.NaN;
def A2L = P2L and IsNaN(AL0) and IsNaN(AL1) and IsNaN(AL2) and IsNaN(AL3) and IsNaN(AL4) and IsNaN(AL5);
def recentHigh = if P2H and PrevP2L then Hi else recentHigh[1];
def AH0 = if P2H and PrevP2H and Hi < recentHigh then 1 else Double.NaN;
def AH1 = if P2H and NextP2H and GetValue(Hi, PivN2h) >= Hi then 1 else Double.NaN;
def AH2 = if p2x2 and PrevP2H and Hi < GetValue(Hi, Piv2h) then 1 else Double.NaN;
def AH3 = if P2H and PrevP2Both and !NextP2L and Hi < GetValue(Hi, Piv2h) then 1 else Double.NaN;
def AH4 = if P2H and PrevP2H and Hi < GetValue(Hi, Piv2h) then 1 else Double.NaN;
def AH5 = if P2H and PrevP2L and NextP2Both and Hi < GetValue(Hi, PivN2h) and GetValue(Lo, PivN2l) > GetValue(Lo, Piv2l) then 1 else Double.NaN;
def A2H = P2H and IsNaN(AH0) and IsNaN(AH1) and IsNaN(AH2) and IsNaN(AH3) and IsNaN(AH4) and IsNaN(AH5);

def PPH = if A2H[1] then 1 else PPH[1] + 1;
def PPL = if A2L[1] then 1 else PPL[1] + 1;
def HighLow = if A2L and Lo > GetValue(Lo, PPL) then 1 else Double.NaN;
def LowHigh = if A2H and Hi < GetValue(Hi, PPH) then 1 else Double.NaN;
def PivTime = if !IsNaN(HighLow) or !IsNaN(LowHigh) then PivTime[1] + 1 else PivTime[1];

#################################################
# Trend Line End Numbers
#################################################
def end1 = if (!IsNaN(HighLow) or !IsNaN(LowHigh)) and PivTime == HighestAll(PivTime) then BarNumber() else 0;
def end2 = if (!IsNaN(HighLow) or !IsNaN(LowHigh)) and PivTime == HighestAll(PivTime) - 1 then BarNumber() else 0;
def end3 = if (!IsNaN(HighLow) or !IsNaN(LowHigh)) and PivTime == HighestAll(PivTime) - 2 then BarNumber() else 0;
def end4 = if (!IsNaN(HighLow) or !IsNaN(LowHigh)) and PivTime == HighestAll(PivTime) - 3 then BarNumber() else 0;
def end5 = if (!IsNaN(HighLow) or !IsNaN(LowHigh)) and PivTime == HighestAll(PivTime) - 4 then BarNumber() else 0;
def end6 = if (!IsNaN(HighLow) or !IsNaN(LowHigh)) and PivTime == HighestAll(PivTime) - 5 then BarNumber() else 0;
def end7 = if (!IsNaN(HighLow) or !IsNaN(LowHigh)) and PivTime == HighestAll(PivTime) - 6 then BarNumber() else 0;
def end8 = if (!IsNaN(HighLow) or !IsNaN(LowHigh)) and PivTime == HighestAll(PivTime) - 7 then BarNumber() else 0;

#################################################
# Trend Line Start Numbers
#################################################
def start1 = if end1 and !IsNaN(HighLow) then end1 - PPL else if end1 and !IsNaN(LowHigh) then end1 - PPH else 0;
def start2 = if end2 and !IsNaN(HighLow) then end2 - PPL else if end2 and !IsNaN(LowHigh) then end2 - PPH else 0;
def start3 = if end3 and !IsNaN(HighLow) then end3 - PPL else if end3 and !IsNaN(LowHigh) then end3 - PPH else 0;
def start4 = if end4 and !IsNaN(HighLow) then end4 - PPL else if end4 and !IsNaN(LowHigh) then end4 - PPH else 0;
def start5 = if end5 and !IsNaN(HighLow) then end5 - PPL else if end5 and !IsNaN(LowHigh) then end5 - PPH else 0;
def start6 = if end6 and !IsNaN(HighLow) then end6 - PPL else if end6 and !IsNaN(LowHigh) then end6 - PPH else 0;
def start7 = if end7 and !IsNaN(HighLow) then end7 - PPL else if end7 and !IsNaN(LowHigh) then end7 - PPH else 0;
def start8 = if end8 and !IsNaN(HighLow) then end8 - PPL else if end8 and !IsNaN(LowHigh) then end8 - PPH else 0;

#################################################
# Price Data
#################################################
def price1 = HighestAll(if end1 and A2L then GetValue(Lo, end1 - start1) else if end1 and A2H then GetValue(Hi, end1 - start1) else 0);
def price2 = HighestAll(if end2 and A2L then GetValue(Lo, end2 - start2) else if end2 and A2H then GetValue(Hi, end2 - start2) else 0);
def price3 = HighestAll(if end3 and A2L then GetValue(Lo, end3 - start3) else if end3 and A2H then GetValue(Hi, end3 - start3) else 0);
def price4 = HighestAll(if end4 and A2L then GetValue(Lo, end4 - start4) else if end4 and A2H then GetValue(Hi, end4 - start4) else 0);
def price5 = HighestAll(if end5 and A2L then GetValue(Lo, end5 - start5) else if end5 and A2H then GetValue(Hi, end5 - start5) else 0);
def price6 = HighestAll(if end6 and A2L then GetValue(Lo, end6 - start6) else if end6 and A2H then GetValue(Hi, end6 - start6) else 0);
def price7 = HighestAll(if end7 and A2L then GetValue(Lo, end7 - start7) else if end7 and A2H then GetValue(Hi, end7 - start7) else 0);
def price8 = HighestAll(if end8 and A2L then GetValue(Lo, end8 - start8) else if end8 and A2H then GetValue(Hi, end8 - start8) else 0);

def price01 = HighestAll(if end1 and A2L then Lo else if end1 and A2H then Hi else 0);
def price02 = HighestAll(if end2 and A2L then Lo else if end2 and A2H then Hi else 0);
def price03 = HighestAll(if end3 and A2L then Lo else if end3 and A2H then Hi else 0);
def price04 = HighestAll(if end4 and A2L then Lo else if end4 and A2H then Hi else 0);
def price05 = HighestAll(if end5 and A2L then Lo else if end5 and A2H then Hi else 0);
def price06 = HighestAll(if end6 and A2L then Lo else if end6 and A2H then Hi else 0);
def price07 = HighestAll(if end7 and A2L then Lo else if end7 and A2H then Hi else 0);
def price08 = HighestAll(if end8 and A2L then Lo else if end8 and A2H then Hi else 0);

#################################################
# Defining Trend Line
#################################################
script trendLine 
{
input startBar = 0;
input startPrice = 0;
input endBar = 0;
input endPrice = 0;
input leftExt = 0;
input rightExt = 0;
input limitRight = no;

def TrendV = (endPrice - startPrice) / (endBar - startBar);
def NewBar = BarNumber() - endBar;
plot TheTrend; if !limitRight then {TheTrend = if BarNumber() >= startBar - leftExt then endPrice + NewBar * TrendV else Double.NaN;} else {TheTrend = if BarNumber() > endBar + rightExt or BarNumber() < startBar - leftExt then Double.NaN else endPrice + NewBar * TrendV;}
}

#################################################
# Trend Lines
#################################################
input howManyTrendLinesMax_8 = 4;

plot Trend1 = trendline(HighestAll(start1), price1, HighestAll(end1), price01, 5, no);
Trend1.SetDefaultColor(Color.WHITE);
Trend1.SetStyle(Curve.FIRM);
plot Trend2 = trendline(HighestAll(start2), price2, HighestAll(end2), price02, 5, no);
Trend2.setDefaultColor(color.WHITE);
Trend2.SetStyle(Curve.SHORT_DASH);
Trend2.SetHiding(howManyTrendLinesMax_8 < 2);
plot Trend3 = trendline(HighestAll(start3), price3, HighestAll(end3), price03, 5, no);
Trend3.SetDefaultColor(color.WHITE);
Trend3.SetStyle(Curve.SHORT_DASH);
Trend3.SetHiding(howManyTrendLinesMax_8 < 3);
plot Trend4 = trendline(HighestAll(start4), price4, HighestAll(end4), price04, 5, no);
Trend4.SetDefaultColor(color.WHITE);
Trend4.SetStyle(Curve.SHORT_DASH);
Trend4.SetHiding(howManyTrendLinesMax_8 < 4);
plot Trend5 = trendline(HighestAll(start5), price5, HighestAll(end5), price05, 5, no);
Trend5.SetDefaultColor(color.WHITE);
Trend5.SetStyle(Curve.SHORT_DASH);
Trend5.SetHiding(howManyTrendLinesMax_8 < 5);
plot Trend6 = trendline(HighestAll(start6), price6, HighestAll(end6), price06, 5, no);
Trend6.SetDefaultColor(color.WHITE);
Trend6.SetStyle(Curve.SHORT_DASH);
Trend6.SetHiding(howManyTrendLinesMax_8 < 6);
plot Trend7 = trendline(HighestAll(start7), price7, HighestAll(end7), price07, 5, no);
Trend7.SetDefaultColor(color.WHITE);
Trend7.SetStyle(Curve.SHORT_DASH);
Trend7.SetHiding(howManyTrendLinesMax_8 < 7);
plot Trend8 = trendline(HighestAll(start8), price8, HighestAll(end8), price08, 5, no);
Trend8.SetDefaultColor(color.WHITE);
Trend8.SetStyle(Curve.SHORT_DASH);
Trend8.SetHiding(howManyTrendLinesMax_8 < 8);

#################################################
# Arrows
#################################################
input showArrows = yes;

#Up Arrows
plot DownArrow1 = Trend1 > Trend1[1] and close crosses below Trend1;
DownArrow1.SetPaintingStrategy(PaintingStrategy.BOOLEAN_ARROW_DOWN);
DownArrow1.SetDefaultColor(color.CYAN);
DownArrow1.SetLineWeight(5);
DownArrow1.SetHiding(!showArrows);

#Down Arrows
plot UpArrow1 = Trend1 < Trend1[1] and close crosses above Trend1;
UpArrow1.SetPaintingStrategy(PaintingStrategy.BOOLEAN_ARROW_UP);
UpArrow1.SetDefaultColor(color.CYAN);
UpArrow1.SetLineWeight(5);
UpArrow1.SetHiding(!showArrows);

#################################################
# Display Box
#################################################
input ShowDisplayBox = yes;
AddLabel(ShowDisplayBox, " ->", color.DARK_GRAY);
AddLabel(ShowDisplayBox, if close > Trend1 then "Above Current Trend" else "Below Current Trend", if close > Trend1 then color.GREEN else color.RED);
AddLabel(ShowDisplayBox, "<- ", color.DARK_GRAY);

#################################################
# Alerts
#################################################
input AudibleAlerts = yes;
Alert(AudibleAlerts and UpArrow1, GetSymbol() + " Possible Breakout.", Alert.BAR, Sound.Bell);
Alert(AudibleAlerts and DownArrow1, GetSymbol() + " Possible Breakdown.", Alert.BAR, Sound.Bell);

#------------------------------------------------------#
#           Auto Trendline Script     	             #
#                                                      #
#------------------------------------------------------#
