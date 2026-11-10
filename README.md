# Composite Filament Extruder

**Peter Cohan** · Home lab · Status: in development

A desktop pellet extruder for making 3D printing filament with controlled additive loadings, starting with chopped carbon fiber in PLA.

## Why This Exists

My [in-line carbon fiber loading experiment](https://github.com/peterccohan/carbon-fiber-inline-loading) showed that loose fiber can't be added at the printer: it reaches the hotend dry, agglomerates, and clogs the nozzle. Fiber has to be compounded into the polymer *before* printing, at a known weight fraction. This extruder is the tool for doing that, so the next round of experiments can compare filament at measured loadings instead of guessing.

This page is a design log. Build progress, CAD, and test data will be added as each stage is completed.

## Design Decisions

| Decision | Chosen | Instead of | Reasoning |
|---|---|---|---|
| Core design | Hybrid built on the [Lyman Filament Extruder V6](#credits) core | Fully original design, or buying a commercial unit | The Lyman barrel, screw, and die layout is proven, so my effort goes into the drive and electronics. Building is also far cheaper than buying. |
| Drive | Two NEMA 17 steppers with MKS SERVO42D closed-loop drivers, through a 3D-printed reduction gearbox | Wiper motor | Closed-loop steppers give a set, repeatable screw speed and can detect stalls. A single NEMA 17 lacks the torque for an auger, so two share the load and the gearbox multiplies it. |
| Gearbox material | PAHT-CF (carbon-fiber nylon) | Standard PLA or PETG | Stiffer and more heat-tolerant than common filaments, which matters for gears under sustained load near a heated barrel. |
| Power | All 24 V DC; heater run from a 30 V bench supply | 120 VAC heater | Keeps mains voltage out of a home-built machine and puts the heater and electronics on one low-voltage system. |
| Budget | About $200 | | Uses motors and supplies already on hand where possible. |

## Requirements for Composite Work

Making filament that's good enough for controlled experiments is harder than making filament that prints. These are the requirements the design has to meet:

- **Diameter control.** The target tolerance is about ±0.05 mm on 1.75 mm filament. Without that, a weak test part could be caused by diameter variation instead of fiber content. This calls for a puller/winder and a diameter sensor in a feedback loop.
- **Dispersion.** A single-screw extruder mixes poorly. Plan: extrude once to compound pellets with fiber, chop the result, and extrude a second time. Cross-sections will be checked for fiber clumping.
- **Abrasion.** Carbon fiber wears screws, barrels, and nozzles, so wetted parts need to be wear-resistant, and wear will be monitored.
- **Dust safety.** Chopped fiber is a fine particulate. Mixing happens wet or enclosed, with a respirator.

## Planned Experiment

1. Make PLA filament at 0%, 2%, 5%, and 10% added carbon fiber by weight.
2. Verify actual fiber content with a matrix burn-off test.
3. Print test specimens with fixed settings.
4. Measure stiffness and strength on a custom test rig.
5. Increase loading until printing fails, to find the clog threshold measured in the [first experiment](https://github.com/peterccohan/carbon-fiber-inline-loading).

## Roadmap

- [ ] Drive and gearbox
- [ ] Barrel, heater, and temperature control (24 V)
- [ ] Puller/winder and diameter measurement
- [ ] First pure-PLA filament run and diameter data
- [ ] Composite filament at controlled loadings
- [ ] Mechanical testing

## Credits

The barrel, screw, and die design builds on Hugh Lyman's Lyman Filament Extruder V6. The drive system, gearbox, and 24 V electronics are my own.

---

*Design and build by Peter Cohan. Write-up drafted with help from Claude (Anthropic) and edited by me.*
