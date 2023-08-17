# Report
## Mode 0:
### Wireless-transmitter:
- Testcase: Send data
  | Info | Verify _Behaviors of Fake RF_transceiver_ |
  | :---:   | :---: | 
  | Data | 60 bytes (0 -> 59) |
  | Channel | 27 |
  | Address | 02 |
- Check list:
  | Check case | Verify _Behaviors of Fake RF_transceiver_ |
  | :---:   | :---: | 
  | AUX is LOW when RF-transceiver receive first byte | ✔️ |
  | Start wireless-transmission (buffer reacch 58 bytes) | ✔️ |
  | AUX is HIGH while module is sending last byte in packet | ✔️ |
  
  + Case 1 (_AUX is LOW when RF-transceiver receive first byte_):
    <p align="center">
    <img src="https://github.com/atfox272/Public-Repo/assets/99324602/7864122c-98eb-4f02-8b25-b3e166ac8fc3" width=70% height=70%>
    </p> 

  + Case 2 (_Start wireless-transmission (buffer reacch 58 bytes)_):
    <p align="center">
    <img src="https://github.com/atfox272/Public-Repo/assets/99324602/78f3122e-9040-4198-b989-b62cced2828e" width=70% height=70%>
    </p> 

  + Case 3 (_AUX is HIGH while module is sending last byte in packet_):
    <p align="center">
    <img src="https://github.com/atfox272/Public-Repo/assets/99324602/1beba64d-39ff-4169-adda-ef9e8eb8fa8a" width=70% height=70%>
    </p> 
    
- Power comsumption:
  | Info | Max value |
  | :---:   | :---: | 
  | Current |  0.8 A |  
  | Voltage |  5V |  
  | Power |  4.0W |

### Wireless-receiver:
- Testcase: Send data
  | Info | Verify _Behaviors of Fake RF_transceiver_ |
  | :---:   | :---: | 
  | Data | 60 bytes (0 -> 59) |

- Check list:
  | Check case | Verify _Behaviors of Fake RF_transceiver_ |
  | :---:   | :---: | 
  | AUX is LOW when RF-transceiver receive first wireless-data | ✔️ |
  | Start sending wireless-data to MCU after 2-3ms | ✔️ |
  | AUX is HIGH when the RF-transceiver finishes sending last wireless-data to MCU | ✔️ |  

  + Case 1 (_AUX is LOW when RF-transceiver receive first wireless-data_):
    <p align="center">
    <img src="https://github.com/atfox272/Public-Repo/assets/99324602/42bae58d-45a5-43dd-ba4d-84dc9a47e733" width=70% height=70%>
    </p> 
  + Case 2 (_Start sending wireless-data to MCU after 2-3ms_):
    <p align="center">
    <img src="https://github.com/atfox272/Public-Repo/assets/99324602/c2712594-18f9-4f3a-b715-2eb0e91201e5" width=70% height=70%>
    </p> 
  + Case 3 (_AUX is HIGH when the RF-transceiver finishes sending last wireless-data to MCU_)
    <p align="center">
    <img src="https://github.com/atfox272/Public-Repo/assets/99324602/2db0da96-45f3-4de2-8d36-afe5426a465d" width=70% height=70%>
    </p> 
- Power comsumption:
  | Info | Max value |
  | :---:   | :---: | 
  | Current |  ➖ A |  
  | Voltage |  5V |  
  | Power |  ➖ W |
  
## Mode 3:
### Set/Get parameter:
- Testcase: Set parameter and Get parameter from transceiver
  | Info | Value |
  | :---:   | :---: | 
  | HEAD | C0 |
  | ADDH | CD |
  | ADDL | AB |
  | SPED | 3D |
  | CHAN | 17 |
  | OPTION | C4 |

- Check-list:
  | Check case | Verify _Behaviors of Fake RF_transceiver_ | Note |
  | :---:  | :---: | :---: | 
  | Save all parameter (C0 - 5 param) | ✔️ | Volatile |
  | Save all parameter (C2 - 5 param) | ✔️ | Volatile |
  | Return parameter (C1 C1 C1) | ✔️ | **Bug of _E32_TTL.h_** : Mode switch (mode3 to others) before receiving all return-parameters |
  | Return version (C3 C3 C3) | ➖ | Not use |
  | Reset (C4 C4 C4) | ✔️ | **Bug of _E32_TTL.h_** : Mode switch (mode3 to others) before reseting completely  |

  * Send & Get parameter (C0 - 5param) (C1 C1 C1):
    <p align="center">
    <img src="https://github.com/atfox272/Public-Repo/assets/99324602/4a33a3e2-ad5f-4f72-873a-90d459682c85" width=70% height=70%>
    <img src="https://github.com/atfox272/Public-Repo/assets/99324602/97835a91-4723-4266-993c-38238c091abe" width=70% height=70%>
    </p> 


  * Reset case (C4 C4 C4)
  <p align="center">
    <img src="https://github.com/atfox272/Public-Repo/assets/99324602/e0ef8aaa-ad62-4f1b-a442-0a6247687ac2" width=70% height=70%>
    </p> 

  
