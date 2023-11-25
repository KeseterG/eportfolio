+++
title="Kyanite"
description="Kyanite is the robot I programmed and assembled for FIRST Robotics Competition 2022 Offseason Competition. It is the last robot I programmed in FRC. Kyanite simplifies many of the concepts raised on Acetate MK2, allowing it to be more robust and accurate from mid to long range while being able to reject wrong cargos inside the ball path. Kyanite also improves the climbing mechanism on Acetate MK2, reduce climb time significantly."
date="2023-08-16"

[taxonomies]
categories=["Project", "Robot"]
skills=["Java", "Control Theory"]

[extra]
byline = "Robust, Accurate Solution for Rapid React."
timeframe = "May 2023 - August 2023"
organization = "IronPulse Robotics - Shanghai Pinghe School"
role = "Team Leader & Lead Programmer"
code_link="https://git.ironpulse.net/IronPulse/2022OffseasonRobot"
title_image = "images/kyanite.jpg"
+++

Kyanite is the fourth and last robot I programmed for [FIRST Robotics Competition (FRC) Season 2022 - Rapid React](https://www.youtube.com/watch?v=LgniEjI9cCM).

Hydrogen is designed to be robust and simple on the field. Based on the innovations on the [Acetate MK2](@/projects/robots/acetate/index.md), we improved the robot's reliability while increasing its scoring limit by changing some of the structures. It is designed to have an intake for collecting cargo, a bidirectional ball path to automatically reject cargo, and a non-turreted shooter to send the cargo into the hub. For the final climbing task, we designed a fast hook-pusher bashed climber to skip the third rung and directly go to the traversal rung.

Kyanite participated in [FRC China Offseason 2023](https://www.thebluealliance.com/event/2023cnsh), and won the competition with Team 8214 and Team 7280 as the 1st Alliance's Captain.

{{ image(name="images/kyanite-on-the-field.jpg", alt="Kyanite on the Field.") }}
{{ caption(caption="Kyanite on the Field.") }}

## Innovations

### Pneumatic-less Design

Kyanite has no pneumatics on it. This allows us to have greater mobility, as the weight occupied by the compressors, tanks, and cylinders is saved. At the same time, we can better control mechanisms' movement (namely the intaker), for more accurate control.

### Automatic Cargo Rejection

During the competition, there is usually a lot of Cargo on the field. The robot must have a certain kind of ability to reject wrong Cargo, as the Cargo of different colors is usually mixed.

To reduce the mind effort requirement on the driver, we designed a fully automatic Cargo rejection system. This system will read the status of the Cargo entering the indexer, and then act based on a Finite State Machine we designed. The ball path will either load, spit (in the direction of the intaker), or eject (in the direction of the ejector) Cargo based on the color and number of Cargo in the ball path.

{{ video(name="videos/auto-ballpath.mp4", alt="Auto BallPath") }}
{{ caption(caption="Auto BallPath Rejection Sample.") }}

### Fast Traversal Climb

We designed a new climbing structure with a combination of a hook (to attach to the highest traversal rung), and a pusher (to adjust Kyanite's posture in air). With the combination of actions of these two structures, Kyanite can climb to the traversal rung in less than 6 seconds.

{{ video(name="videos/fast-traversal.mp4", alt="Fast Traversal Climb On the Field!") }}
{{ caption(caption="Fast Traversal Climb On the Field!") }}

### Auto

With the support of ["Codeless" Autonomous](@/projects/robots/acetate/index.md#codeless-autonomous), the development of autos becomes easy. We designed 5 different sets of autonomous, suitable for different starting points, allowing us to have better coordination with our teammates.

## Development Story

The time we started to develop Kyanite was around late May. Due to various reasons, the offseason competition held in August is not going to be themed in 2023 (Charged Up), but in 2022 (Rapid React). This might be the last Rapid React competition for FRC.

During May, we settled on the concept of building a non-turreted robot for simplicity. At the same time, to improve the old robot, we decided to mainly innovate in 3 aspects:

1. The Intaker. The mechanism we originally designed is ineffective, as it does not provide enough compression against the cargo. At the same time, the intake uses the only pneumatic cylinder on the robot, which can be improved and removed to lower the robot's weight and thus increase the maximum speed of the robot.
2. The Climber. Although the old mechanism is enough to climb the traversal rung, the 13-second climb time is a bit long. At the same time, the climbing process is pretty violent, causing a lot of stress on the supporting structure. One of the times, the whole structure bends due to the violent force exerted on the structure. We want to build a more simple and effective structure for climbing.
3. The Ballpath. The old ball path is not able to handle the wrong Cargo and is prone to getting stuck under large forces. We want to build a more effective ballpath structure.

With all the factors combined, we took inspiration from [1678's Robot Margie](https://www.citruscircuits.org/2022_robot.html), and implemented our version.

During testing, as we still didn't have our field, we went to another city for 5 days for testing and improvements. After that period, we went back and finalized the robot at our temporary base, and finally went to the competition.

{{ image(name="images/dt-badges.jpg", alt="Drive Team Badges.") }}
{{ caption(caption="Drive Team Badges.") }}
