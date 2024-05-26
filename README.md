
**DANE KONTAKTOWE**

Jan Stryszewski[yanco@student.agh.edu.pl] Jakub Pietrzko[pietrzko@student.agh.edu.pl]

**OPIS**

Aktywny tepompomat to zaawansowany system wspomagający kierowcę, który utrzymuje ustawioną prędkość jazdy, automatycznie dostosowuje prędkość pojazdu do warunków ruchu drogowego, śledząc odległość do pojazdu jadącego przed nim i regulując prędkość w celu zachowania bezpiecznej odległości. Dodatkowo, system jest wyposażony w funkcjonalność kontroli pasa ruchu, która monitoruje i koryguje położenie pojazdu względem oznakowania poziomego dróg, zapewniając, że pojazd pozostaje w swoim pasie.

 **DANE**

**bool_type:**

  * Opis: Typ danych reprezentujący wartość logiczną.
  * Rozmiar: 16 bitów.
**float_type:**

  * Opis: Typ danych reprezentujący wartość zmiennoprzecinkową.
  * Rozmiar: 32 bity.
**image_type:**

  * Opis: Typ danych reprezentujący obraz.
  * Rozmiar: 1024 bajty.
**URZĄDZENIA**

**cruise_control_button:**

  * Opis: Przycisk do włączania/wyłączania tempomatu.
  * Porty: cc_system_on_off (wyjście danych, typ logiczny).
  * Właściwości: MIPSBudget = 0.1 mips, RAMBudget = 1.0 KByte.
**brake_pedal:**

  * Opis: Pedał hamulca.
  * Porty: brake_status (wyjście danych, typ logiczny).
  * Przepływy: Flow1 (źródło przepływu z opóźnieniem 10ms).
  * Właściwości: MIPSBudget = 0.2 mips, RAMBudget = 1.0 KByte.
**wheel_rotation_sensor:**

  * Opis: Czujnik obrotu koła.
  * Porty: wheel_pulse (wyjście danych, typ zmiennoprzecinkowy).
  * Właściwości: MIPSBudget = 0.2 mips, RAMBudget = 1.0 KByte.
**throttle_actuator:**

  * Opis: Siłownik przepustnicy.
  * Porty: throttle_setting (wejście danych, typ zmiennoprzecinkowy).
  * Przepływy: Flow1 (ujście przepływu z opóźnieniem 20ms).
  * Właściwości: MIPSBudget = 0.3 mips, RAMBudget = 1.0 KByte.
**engine:**

  * Opis: Silnik.
  * Porty: engine_status (wyjście danych, typ logiczny).
  * Właściwości: MIPSBudget = 0.1 mips, RAMBudget = 1.0 KByte.
**resume_button:**

  * Opis: Przycisk wznowienia.
  * Porty: resume (wyjście danych, typ logiczny).
  * Właściwości: MIPSBudget = 0.1 mips, RAMBudget = 1.0 KByte.
**speed_up_button:**

  * Opis: Przycisk zwiększenia prędkości.
  * Porty: increase_speed (wyjście danych, typ logiczny).
  * Właściwości: MIPSBudget = 0.1 mips, RAMBudget = 1.0 KByte.
**speed_dn_button:**

  * Opis: Przycisk zmniejszenia prędkości.
  * Porty: decrease_speed (wyjście danych, typ logiczny).
  * Właściwości: MIPSBudget = 0.1 mips, RAMBudget = 1.0 KByte.
**radar_sensor:**

  * Opis: Radar.
  * Porty: distance_to_vehicle (wyjście danych, typ zmiennoprzecinkowy), busAccess (dostęp do szyny, PC104_ISA_16BIT).
  * Właściwości: MIPSBudget = 0.2 mips, RAMBudget = 1.0 KByte.
**lane_camera:**

  * Opis: Kamera pasa.
  * Porty: lane_image (wyjście danych, typ obraz), busAccess (dostęp do szyny, PC104_ISA_16BIT).
  * Właściwości: MIPSBudget = 0.3 mips, RAMBudget = 1.0 KByte.
**lane_departure_warning_actuator:**

  * Opis: Siłownik ostrzegający o opuszczeniu pasa.
  * Porty: lane_warning_signal (wejście danych, typ logiczny), busAccess (dostęp do szyny, PC104_ISA_16BIT).
  * Właściwości: MIPSBudget = 0.2 mips, RAMBudget = 1.0 KByte.
**vibration_motor:**

  * Opis: Silnik wibracyjny.
  * Porty: vibration_signal (wejście danych, typ logiczny), busAccess (dostęp do szyny, PC104_ISA_16BIT).
  * Właściwości: MIPSBudget = 0.2 mips, RAMBudget = 1.0 KByte.
**auditory_warning_system:**

  * Opis: System ostrzegania dźwiękowego.
  * Porty: auditory_signal (wejście danych, typ logiczny), busAccess (dostęp do szyny, PC104_ISA_16BIT).
  * Właściwości: MIPSBudget = 0.2 mips, RAMBudget = 1.0 KByte.
**visual_alert_system:**

  * Opis: System ostrzegania wizualnego.
  * Porty: visual_signal (wejście danych, typ logiczny), busAccess (dostęp do szyny, PC104_ISA_16BIT).
  * Właściwości: MIPSBudget = 0.2 mips, RAMBudget = 1.0 KByte.
**KOMPONENTY OPROGRAMOWANIA**
**in_control:**

  * Opis: Moduł sterowania.
  * Porty: cc_system_on_off, brake_status, resume, decrease_speed, increase_speed, set_speed, engine_status (wszystkie wejścia danych, typ logiczny), ok_to_run (wyjście danych, typ logiczny).
  * Przepływy: FS1 (przepływ ścieżki z opóźnieniem 30ms).
  * Właściwości: MIPSBudget = 0.5 mips, RAMBudget = 1.0 KByte.
**compute_velocity:**

  * Opis: Moduł obliczania prędkości.
  * Porty: wheel_pulse (wejście danych, typ zmiennoprzecinkowy), instantaneous_velocity (wyjście danych, typ zmiennoprzecinkowy).
  * Przepływy: FS1 (przepływ ścieżki).
  * Właściwości: MIPSBudget = 0.4 mips, RAMBudget = 1.0 KByte.
**compute_desired_speed:**

  * Opis: Moduł obliczania żądanej prędkości.
  * Porty: ok_to_run (wejście danych, typ logiczny), instantaneous_velocity, previous_instantaneous_velocity (wejście danych, typ zmiennoprzecinkowy), current_instantaneous_velocity, desired_speed (wyjście danych, typ zmiennoprzecinkowy).
  * Przepływy: FS1 (przepływ ścieżki z opóźnieniem 40ms), FS2 (przepływ ścieżki).
  * Właściwości: MIPSBudget = 0.5 mips, RAMBudget = 1.0 KByte.
**compute_throttle_setting:**

  * Opis: Moduł obliczania ustawienia przepustnicy.
  * Porty: desired_speed (wejście danych, typ zmiennoprzecinkowy), throttle_setting (wyjście danych, typ zmiennoprzecinkowy).
  * Przepływy: FS1 (przepływ ścieżki z opóźnieniem 50ms).
  * Właściwości: MIPSBudget = 0.5 mips, RAMBudget = 1.0 KByte.
**active_cruise_control:**

  * Opis: System aktywnego tempomatu.
  * Porty: distance_to_vehicle, desired_speed (wejście danych, typ zmiennoprzecinkowy), adjusted_speed (wyjście danych, typ zmiennoprzecinkowy).
  * Przepływy: FS1 (przepływ ścieżki).
  * Właściwości: MIPSBudget = 0.6 mips, RAMBudget = 1.0 KByte.
**lane_control_module:**

  * Opis: Moduł kontroli pasa ruchu.
  * Porty: lane_warning_signal (wejście danych, typ logiczny), lane_warning_output (wyjście danych, typ logiczny).
  * Przepływy: FS1 (przepływ ścieżki).
  * Właściwości: MIPSBudget = 0.4 mips, RAMBudget = 1.0 KByte.
**lane_departure_detection_system:**

  * Opis: System wykrywania opuszczenia pasa.
  * Porty: lane_image (wejście danych, typ obraz), lane_warning_signal (wyjście danych, typ logiczny).
  * Przepływy: FS1 (przepływ ścieżki).
  * Właściwości: MIPSBudget = 0.4 mips, RAMBudget = 1.0 KByte.
**DEKLARACJE SYSTEMU**

**cc_app:**
  * Opis: Aplikacja tempomatu.
  * Porty: device_bus (wymaga dostępu do szyny, PC104_ISA_16BIT).
  * Właściwości: MIPSCapacity = 3.0 mips.
**DEKLARACJE PLATFORMY SPRZĘTOWEJ**

**PC104_ISA_16BIT:**

  * Opis: Magistrala PC104 ISA 16-bit.
  * Właściwości: BandWidthCapacity = 2.0 MBytesps, BandWidthBudget = 200.0 KBytesps.
**SDRAM:**

  * Opis: Pamięć SDRAM.
  * Porty: controller_memory (wymaga dostępu do szyny, PC104_ISA_16BIT).
  * Właściwości: RAMCapacity = 4.0 GByte.
**PENTIUM:**

  * Opis: Procesor Pentium.
  * Porty: controller_cpu (wymaga dostępu do szyny, PC104_ISA_16BIT).
  * Właściwości: Scheduling_Protocol = Round_Robin_Protocol, Clock_Period = 1ms, Processor_Capacity = 1.0 MIPS, MIPSCapacity = 5.0 mips.
**Systemy**

**cruise_control:**

  * Opis: System kontroli prędkości.
  * Porty: cc_system_on_off, engine_status, brake_status, resume, decrease_speed, increase_speed, set_speed (wszystkie wejścia danych, typ logiczny), wheel_pulse, distance_to_vehicle (wejście danych, typ zmiennoprzecinkowy), lane_image (wejście danych, typ obraz), throttle_setting, lane_warning_signal (wyjście danych, typ logiczny).
  * Przepływy: brake_flow_1 (przepływ ścieżki).
**cruise_control.impl:**

  * Opis: Implementacja systemu kontroli prędkości.
  * Subkomponenty: I_C, C_V, C_D_S, C_T_S, ASC, LCM, LDDS, RADAR, LANE_CAMERA, LANE_WARNING, VIBRATION_MOTOR, AUDITORY_WARNING, VISUAL_ALERT, AGH_memory, AGH_bus, AGH_processor.
  * Połączenia: C1 - C30.
  * Właściwości: Wiązania procesora, pamięci i połączeń do odpowiednich komponentów.
**cc_app.impl:**

  * Opis: Implementacja aplikacji kontroli prędkości.
  * Subkomponenty: CC, BRAKE, TA, CC_ON_OFF, ENGINE, RESUME, SP_UP, SP_DN, WHEEL_ROT_SENSOR, RADAR, LANE_CAMERA, LANE_WARNING, VIBRATION_MOTOR, AUDITORY_WARNING, VISUAL_ALERT.
  * Połączenia: C21 - C37.
  * Właściwości: Wiązania procesora, pamięci i połączeń do odpowiednich komponentów.
**cc_computer:**

  * Opis: Komputer tempomatu.
  * Porty: device_bus (zapewnia dostęp do szyny, PC104_ISA_16BIT).
  * Właściwości: MIPSCapacity = 1.5 mips.
**AGH_cruise_control_system:**

  * Opis: System system tempomatu AGH.
  * Właściwości: MIPSCapacity = 2.4 mips.
**cc_computer.AGH:**
  * Opis: Implementacja komputera AGH.
  * Subkomponenty: AGH_memory, AGH_bus, AGH_processor.
  * Połączenia: C1 - C3.
**AGH_cruise_control_system.impl:**

  * Opis: Implementacja systemu kontroli prędkości AGH.
  * Subkomponenty: AGH_computer, AGH_software.

