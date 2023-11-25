+++
title="Acetate"
description="Acetate is the robot I programmed and assembled for FIRST Robotics Competition 2022. It utilizes control theory, localization techniques, and design in software structuring to reach a high level of automation. The development process of Acetate is done over the year 2022 under the COVID pandemic."
date="2022-03-05"

[taxonomies]
categories=["Project", "Robot"]
skills=["Java", "Control Theory"]

[extra]
byline = "Turreted, Agile and Fast Solution for Rapid React."
timeframe = "January 2022 - December 2022"
organization = "IronPulse Robotics - Shanghai Pinghe School"
title_image = "images/acetate-square.jpg"
role = "Team Lead & Lead Programmer"
+++

Acetate is the second robot I programmed for [FIRST Robotics Competition (FRC) Season 2022 - Rapid React](https://www.youtube.com/watch?v=LgniEjI9cCM). It is also the first robot I independently programmed as the team's programming lead.

Acetate is designed to be a fast, accurate, mid-to-long-range scorer. Cargo is the target gamepiece in Rapid React, which is similar to an inflated tennis at the size of a basketball. To score cargo into the target - a 2.5 meter high, 1.2 meter wide hub, acetate is equipped with a custom metric swerve drivetrain at a free speed of 4.0 meters per second, along with a turreted shooter with {{ katex(body="\pm 150 ^{\circ}") }} of rotation range and {{ katex(body="30^{\circ}") }} of backboard adjustment range. Such design allows acetate to aim and score at more than 80% of the positions on the field.

For the end game of Rapid React, Acetate is required to climb a "monkey bar" consisting of 4 sub-bars, the higher bars will lead to great endgame point gains. For accomplishing this task, Acetate is also equipped with a single staged elevator along with a pneumatically actuated hooker for a switch-and-climb routine to the highest bar.

Acetate marks a great leap in my Robotics ability. Starting from this robot, I became fluent in Java Programming and gained rich experience in refactoring, structuring, and debugging. At the same time, Acetate allows me to apply control theories and algorithms on a real robot for the first time to improve its performance.

{{ image(name="images/acetate-in-action.jpg", alt="Acetate in Action") }}
{{ caption(caption="Acetate in Action.") }}

## Innovations

### State Machine

State Machine is a widely used tool for building robotics intelligence. State machine defines a system into a definite number of states, robots will carry out desired actions under each state. The transition of states will be triggered by actions or events, also triggering potential changes along the way.

Acetate's superstructure, along with its ball path & climbing mechanism, is designed using state machines. This allows Acetate to have different modes to handle various situations systematically.

{{ two(name1="images/superstructure-state.jpg", alt1="Superstructure State", name2="images/ballpath-state.jpg", alt2="BallPath State") }}

{{ caption(caption="State Diagram for Acetate's Superstructure and Ballpath") }}

Most of the automation is based on the use of state machines. One of the examples is the implementation of automatic wrong-cargo rejection. Via the coordination among the turret, shooter, and ballpath, wrong cargo can be ejected to any point on the field. Another example is the automatic climbing sequence, allowing Acetate to reach the highest rung in 12 seconds.

{{ video(name="videos/auto-rejection.mp4") }}
{{ caption(caption="Auto-Rejection Example.") }}


### Simulation & Modeling

Before the start of the design of Acetate MK2, I finished an essay on calculating the optimal trajectory of the Cargo.

During the launch of the Cargo, there are several key parameters: the angle of the turret, the angle of the backboard, and the rotational velocity of the flywheel. These three components build up a vector in space, determining the initial launching force for the Cargo.


{{ two(name1="images/4d-graph.png", alt1="4D Graph", name2="images/possible_trajectories.png", alt2="Trajectories") }}

{{caption(caption="Left: All Potential State Combination; Right: Possible Trajectories at Different Distances.")}}

Using the physical model and numerical method for optimization, the optimal combination of launching state that leads to minimum cost is generated. This gives a good reference point for our mechanism design & iteration.

### Feedforward & Tangential Speed Compensation

Characterization is done on the turret and drivetrain to determine their velocity and acceleration feedforward constants. Then, by using a linear model and feeding the result using voltage, the movement of these two mechanisms takes into more control inputs and is more responsive to the change of target. This, in turn, results in heightened accuracy, efficiency, and overall performance of the turret and drivetrain within the larger system.

{{katex(body="V = K_s + K_v v + K_a a", block=true)}}

At the same time, the robot's velocity with respect to the target is compensated.

### Localization

The localization of Acetate is based on the Extended Kalman Filter (EKF). The localizer receives an update from the odometry of the swerve drivetrain for high-frequency local updates and adjusts the measurement using gyro and camera feedback with a changing covariance. The usage of EKF gives Acetate the ability to fuse multiple measurements effectively, allowing it to find its position on the whole field at any time.

To provide more accurate observation, an anti-distortion is used on the camera. Every measured point of the vision target will first be through this step before it is calculated and fed into the EKF. The anti-distortion used a quadratic to model the distortion, and the constants of distortion were measured and fitted using a chessboard.


{{ two(name1="images/fusion-interface.png", alt1="Localization Interface", name2="images/anti-dis.png", alt2="Anti Distortion") }}
{{caption(caption="Left: EKF Localization Interface; Right: Anti-Distortation Model")}}

With the aid of localization, Acetate can accurately find its velocity with respect to the vision target. Combined with feedforward, the allows Acetate to have the ability to "move-and-shoot".

{{ video(name="videos/move-and-shoot.mp4") }}
{{ caption(caption="Move and Shoot Demonstration.") }}

### "Codeless" Autonomous

Finally, combining those abilities, Acetate is given the power to reach a high level of automation during the autonomous phase. Most of the functions are highly automated, thus the coding for the autonomous stage becomes too simple. Using the [PathPlanner](https://github.com/mjansen4857/pathplanner) tool, we can set up autonomous modes without any actual coding.

In total, Acetate is equipped with 10 autonomous modes, ranging from simple shoot-the-preload to complex 7-ball autonomous. The program will automatically scan all the path configuration files, read the trajectories and corresponding timepoints, finally load them, and get them ready for selection on the dashboard on the operator side.

Below is the showcase of two advanced autonomous routines: steal autonomous (go to the opponent's field for their cargo) and 7 ball autonomous (6 self-cargo, 1 opponent's cargo).

{{ video(name="videos/steal.mp4") }}
{{ caption(caption = "Steal Autonomous. Time: 7.99''")}}
{{ video(name="videos/6+1.mp4") }}
{{ caption(caption = "6+1 Autonomous. Time: 14.74''")}}

## Development Story

Acetate's development takes a whole year. The main reason for this, of course, is the COVID-19 pandemic. As our team is based in Shanghai, we had undergone a lockdown from mid-March to late July, and the effect of the pandemic continued even after the lockdown. Due to this, Acetate is not able to attend any competition - because there isn't one available during that special period.

One of the other constraints we have under such a situation is our field. Our shop's height is not enough to shoot the Cargo, so we have to find other places for testing and practice. This made the process of building Acetate even harder.

Even with those constrictions, our team finished 10+ small iterations on Acetate and 2 major iterations (MK1 and MK2) on Acetate. We discovered the problems during designing, assembling, and finally testing & debugging.

### Acetate MK1: Turret Tests, Basic Vision Aim, Software Framework

During the first design stage, our team discussed and settled down the design goals we have for FRC Season 2022.

We described the competition with these words: fast-paced, violent, strong-defensive, and agile (this makes me consider Rapid React to be one of the best names for FRC games). Due to those requirements, a turret becomes a must, as it can help our robot to aim at the target even under heavy defense. To leave space for the turret, the climbing mechanism needs to be compact. Finally, the whole robot combined should have a really low center of gravity, to counteract tipping caused by all the potential collisions. 

This led to the first version of our robot design. Our robot uses the old 2021 drivetrain from [Zorro](@/projects/robots/zorro/index.md), but with an increased width of the traction thread from 1 inch to 1.5 inch. This brings higher traction and thus more stability and counter-defense abilities.

For the robot's Superstructure, we have a simple pneumatically actuated intake, equipped with mecanum wheels for automatic cargo centering. The end of the ballpath is equipped with a turret without a backboard, so it will be simple enough for our team to make.

Acetate MK1 is assembled during the winter vacation and the first month of the 2022 spring semester.

### Acetate MK2: Increase Turret Angle, Complex Control, Autonomous

During the build season, we realized some of the drawbacks of our design. The backboard is far more important than we originally considered, as it can significantly increase the locations where the robot can shoot the cargo. At the same time, we find the simple mecanum intake is prone to breaking under high-speed collisions. This leads to the various improvements made on Acetate MK2, whose features are shown in the previous passage.

### The End of FRC 2022

Unfortunately, till the very end of the year 2022, the opportunity for competition does not come. Acetate is not able to compete in any of the formal competitions, but only in one online regional competition.

During the online regional, Acetate and IronPulse Robotics won the Autonomous Award for FRC Hangzhou Regional 2022 (online).

This is surely a bitter end, as my whole year of work ends in nearly vain. However, Acetate still means a lot to me, as it helps me to grow my understanding of Robotics. This prepares me for competition season 2023 and my future career in Robotics and Autonomous Systems.

{{ image(name="images/acetate-on-run.jpg", alt="Acetate on Run") }}
{{ caption(caption="Acetate MK2, Shot on One of the Shop Nights.") }}
