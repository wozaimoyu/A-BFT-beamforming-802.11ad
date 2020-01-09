# Introduction:
This is a Python implementation of the IEEE 802.11ad A-BFT beamforming training medium access protocol.

In order to study the performance of IEEE 802.11ad A-BFT beamforming training, 
we developed a discrete-event time-driven custom simulator in Python that implements the A-BFT medium access protocol.
It closely follows the IEEE 802.11ad standard's specifications for each independently transmitting station.

We model an Responder Sector Sweep (RSS) as a single frame transmission occupying one time slot. 
A station succeeds a RSS attempt only if it receives a feedback frame from the AP before the end of the ongoing time slot. 
If no collisions occur, the RSS is successful. 
We abstracted the feedback mechanism  and instead kept count of the number of colliding stations in each time slot to determine a RSS failure. 
We consider the transmission channel ideal so that RSS failures are due to collisions only.

# Features:
All protocol parameters can adjusted: the number of slots per period, the maximum number of successive attempts, the idle backoff window  and simulation time in periods.

We also log a set of statistics including but not limited to:
- Average number of periods before a station succeeds its RSS
- Average number of periods until a station becomes idle
- Success rate in a period
- Probability of success of a RSS
- Probability a station is idle
- Probability distribution of success and idle.

The above results can be logged to a file using the `--tofile` option. 

# Requirements:
A working installation of Python 2 with the following modules are required:
- numpy
- collections

# Usage:
`python abft-simulation.py --help`

# Example:
`python abft-simulation.py 20 8 4 2 --time 1000000` is a 1000000 periods simulation run with 20 stations, 8 time slots per period, 4 maximum allowed consecutive attempts and an idle backoff window of 2.
