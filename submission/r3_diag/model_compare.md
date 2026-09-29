# L / R / M

L/R/M là thứ tự box in-scope theo XML của từng frame.

## adasind_258420.jpg
- L4+R4: LR_noM (center)
- L5+R1: LR_noM (edge)
- L6+R6+M2: LRM (edge)
- L9+R8: LR_noM (center)
- L2+R3+M3: LRM (mid)
- L1+R2+M9: LRM (mid)
- L3: L_only (mid)
- L7: L_only (mid)
- L8+M6: LM_noR (mid)
- R5: R_only (mid)
- R7+M12: RM_noL (mid)
- M4: M_only (edge)
- M5: M_only (mid)
- M7: M_only (mid)
- M8: M_only (center)
- M10: M_only (mid)
- M11: M_only (center)
## adasind_270517.jpg
- L2+R6+M1: LRM (mid)
- L6+R2: LR_noM (center)
- L1+R4: LR_noM (center)
- L7+R3+M2: LRM (edge)
- L4+R1+M4: LRM (center)
- L3+R5+M3: LRM (center)
- R7+M8: RM_noL (mid)
- M5: M_only (mid)
- M6: M_only (center)
- M7: M_only (center)
- M9: M_only (center)
- M10: M_only (mid)
- M11: M_only (mid)
## adasind_310008.jpg
- L4+R1: LR_noM (mid)
- L3+R2+M3: LRM (edge)
- L2+R3+M1: LRM (edge)
- L5+R4+M4: LRM (edge)
- L1+R5+M2: LRM (edge)
- M6: M_only (mid)
- M7: M_only (mid)

## Zone × cell
| zone | LRM | LR_noM | LM_noR | L_only | RM_noL | R_only | M_only |
|---|---|---|---|---|---|---|---|
| center | 2 | 4 | 0 | 0 | 0 | 0 | 5 |
| mid | 3 | 1 | 1 | 2 | 2 | 1 | 8 |
| edge | 6 | 1 | 0 | 0 | 0 | 0 | 1 |
