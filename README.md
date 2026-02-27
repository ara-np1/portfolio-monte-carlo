# portfolio-monte-carlo
Monte Carlo portfolio simulator
# Portfolio Monte Carlo Simulator

A Python tool simulating 5-year performance of a diversified global 
portfolio across 18 assets using Monte Carlo methods.

## What it does
- Downloads live price data via yfinance
- Runs 10,000 simulations using log-normal return modelling
- Computes VaR, CVaR, Sharpe Ratio and Sortino Ratio
- Outputs a distribution histogram with annotated risk metrics

## Technologies
Python · NumPy · Matplotlib · yfinance

## How to Run
pip install numpy matplotlib yfinance
python monte_carlo.py

## Nederlands
Dit programma is ontworpen om de onzekerheid van de markt te vangen in tienduizend verschillende scenario's. In plaats van te rekenen met vaste gemiddelden, gebruikt de code live data van achttien verschillende assets om een realistisch beeld te schetsen van de komende vijf jaar. Via yfinance worden de meest recente koersen binnengehaald, waarna de code zelf de rendementen en volatiliteit berekent. Dit zorgt ervoor dat de simulatie altijd gebaseerd is op de huidige marktomstandigheden en niet op verouderde aannames.

De kern van de nauwkeurigheid zit in de correlatiematrix. In de echte wereld bewegen assets niet onafhankelijk van elkaar; als de S&P 500 hard valt, gaan tech-aandelen vaak mee. Door een Cholesky-decompositie toe te passen op deze matrix, dwing ik de simulatie om deze onderlinge afhankelijkheden te respecteren. Dit voorkomt dat de tool een te optimistisch beeld schetst door te doen alsof risico’s altijd perfect gespreid zijn.

Voor de simulaties zelf is gekozen voor de Geometrische Brownse Beweging (GBM). Dit is een wiskundig model dat rekening houdt met het feit dat rendementen log-normaal verdeeld zijn. Hierdoor worden onrealistische uitschieters door compounding gecorrigeerd. Met np.cumprod worden deze jaarlijkse schommelingen samengevoegd tot een eindwaarde per scenario.

Om de resultaten bruikbaar te maken, berekent de code statistieken zoals de Value at Risk (VaR) en de Sortino-ratio. De VaR laat zien wat het minimale verlies is in de slechtste 5% van de marktomstandigheden, terwijl de Sortino-ratio de nadruk legt op neerwaarts risico in plaats van algemene volatiliteit. Het histogram aan het eind groepeert de tienduizend uitkomsten, zodat je in één oogopslag de waarschijnlijkheid van verschillende scenario's ziet, inclusief de mediaan en de kans op verlies.

## English
This program is designed to capture market uncertainty across ten thousand different scenarios. Instead of relying on fixed averages, the code uses live data from eighteen different assets to project a realistic five-year outlook. By integrating yfinance, the tool fetches the latest market prices and automatically calculates returns and volatility, ensuring the simulation is always grounded in current market conditions.

The technical core of the model lies in the correlation matrix. Assets do not move independently; if the S&P 500 drops significantly, tech stocks usually follow. By applying a Cholesky Decomposition to this matrix, the simulation is forced to respect these interdependencies. This prevents the model from being overly optimistic by assuming risks are always perfectly diversified.

The simulations are built on Geometric Brownian Motion (GBM), a mathematical model that accounts for the log-normal distribution of returns. This correction is vital to prevent unrealistic compounding effects over the five-year horizon. Using np.cumprod, these annual fluctuations are compounded into a final portfolio value for each of the ten thousand paths.

To turn this raw data into insights, the code calculates metrics like Value at Risk (VaR) and the Sortino Ratio. The VaR identifies the minimum loss in the worst 5% of market conditions, while the Sortino Ratio focuses specifically on downside risk rather than general volatility. The final histogram groups the ten thousand outcomes, providing a clear visual representation of the probability distribution, including the median and the likelihood of a loss.
