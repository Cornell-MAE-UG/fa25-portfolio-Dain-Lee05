---
layout: project
title: Human Heart
description: MAE 3260 Final Groupwork
technologies: [MATLAB, python]
image: /assets/images/human heart.png
---
MAE 3260 Final Group Work: Exploring a System of Interest

Outline:
<br>Page 1: Cover page
<br>Page 2: The Heart System
<br>Pages 2-4: ODE Model for Human Heart
<br>Pages 4-6: Performance Requirements
<br>Page 6-7: Cardiovascular Disease
<br>Page 8-10: ICD: Medical Remedy
<br>Page 10-11: References
<br>Page 11-13: Appendix (contains Matlab Code)

Title: The Heart as a System

Topic of Interest: Human Heart

Abstract: In this project, we will be studying the human heart as a system. Specifically, we will be looking into devices that aid in its function in the case of disease and their respective effects on the cardiovascular system to satisfy performance metrics. In terms of system dynamics, we will be analyzing the heart through a block diagram, state space model, and closed loop control system. We are interested in connecting system dynamics to biology, since we have not done that in the scope of the course. 

<The Heart System>
<br>The heart and circulatory system is modeled as a closed loop system with a purpose of delivering oxygenated blood to muscles throughout the body. More specifically, the system starts with veins bringing deoxygenated blood towards the heart. Eventually the blood enters the heart through the right atrium and flows into the right ventricle. From there, the blood travels to the lungs to dispose of waste products, notably carbon dioxide, and pick up oxygen. The newly oxygenated blood enters the left atrium followed by the left ventricle. From there, the blood circulates to the rest of the body via arteries [1]. 
<br>It can be convenient to compare the heart as a system via a block diagram of sorts. They can be thought of as inputs, deoxygenated blood, and outputs, oxygenated blood, with the heart transferring the blood in between. 

![Shaded rendering of earlier version]({{ "/assets/images/fig1.png" | relative_url }}){: .inline-image-c style="width: 500px"}

Figure 1: Block Diagram of the Heart [2]

<ODE Model for Human Heart>
<br>After understanding, biologically, what is occurring in the heart, our group wanted to characterize the system in a way that made sense for system dynamics. A logical first step was to develop an ODE(s) to describe the system. It was helpful to do research on if this was done before or if there is an existing model that is commonly used. As it turns out, in bioengineering a common model is that of the Windkessel Model [3]. In this model, the circulatory system is treated as an electrical system.

![Shaded rendering of earlier version]({{ "/assets/images/fig2.png" | relative_url }}){: .inline-image-c style="width: 500px"}

Figure 2: Table Representing the Windkessel Model of the Heart [4]


Upon further research, it seemed that this model was a bit above the scope of this assignment and our knowledge, so we decided to fit an ODE to data of heart rate. This still allows us to develop a deeper understanding of the heart as a system. 
Finding applicable data to even fit an ODE to was a larger challenge than anticipated. Significant data was presented in unusable forms that did not translate to data that can be analyzed by Matlab. Eventually, a data set was found that tracked the heart rate of a healthy 49 year old man practicing Chi Yoga. This heart rate data is considered to be a good baseline of a “normal” resting heart rate. There are numerous extraneous inputs, such as diseases, exercise and cardiac devices, that can lead to different heart rates, but in this data set, those are not present. It should be noted that Matlab code used for this analysis is appended at the end of the report [5].

![Shaded rendering of earlier version]({{ "/assets/images/fig3.png" | relative_url }}){: .inline-image-c style="width: 500px"}

Figure 3: Zoomed in Heart Rate Raw Data Plotted

![Shaded rendering of earlier version]({{ "/assets/images/fig4.png" | relative_url }}){: .inline-image-c style="width: 500px"}


Figure 4: Fitted ODE plotted against data


In conclusion, this ODE is not very accurate for a simple resting heart rate. For future reference, it could be interesting to fit an ODE for how heart rate changes during the beginning or end of a workout, such as “ramping up” the input.

<Performance Requirements>
<br>To design any closed loop system for the heart and cardiovascular system, we need defined performance requirements that show what an ideal and healthy operation looks like. These requirements act as constraints and describe allowable steady state values, acceptable behavior, and error tolerances for a model. It allows us to know what the output should be so that we can adjust a controller, like an ICD or pacemaker, to drive and stabilize the system to our desired goals.

The main performance requirement that our model utilizes is heart rate. For a healthy adult's heart rate at rest, the value ranges between 60 to 100 beats per minute [12]. This defines the steady state value for the heart rate ODE so when the system is disturbed then the controller should drive the heart rate back to its ideal range. Since this requirement is the primary output in our model it is clear to see when an acceptable or unacceptable output occurs. Any significant deviations from the ideal heart rate may indicate problems such as tachycardia or other arrhythmias. 

Another performance requirement that determines healthy cardiac operation is blood pressure. The heart blood pressure is the force of blood that pushes against the artery walls while the heart pumps blood throughout the body. It is measured with systolic pressure, the force of blood against artery walls when the heart contracts, and diastolic pressure which is the pressure in arteries when the heart relaxes between beats. For a healthy adult the systolic pressure should be less than 120 mmHg and the diastolic pressure less than 80 mmHg [13]. If there is an elevated pressure then the heart would have to work harder which could change the system's behavior or parameters, requiring more control input to maintain a normal heart rate. This essentially acts as an external disturbance that can alter the steady state value and gain. 

An additional performance requirement is the stroke volume. This is defined as the amount of blood pumped by the left ventricle per beat and for a healthy heart the stroke volume is around 70 mL, but a normal range is between 50 to 100 mL [14]. If the stroke volume is low then the heart would not pump much blood per beat which reduces the system's output for a given heart rate. This would require the heart rate to increase in order to maintain its cardiac output. On the other hand, if the stroke volume is high then the heart would pump a lot of blood per beat and increase the system’s output. Thus the stroke volume impacts the gain of the system.

The last performance requirement that was researched is the cardiac output. Similar to the stroke volume, the cardiac output is the total volume of blood pumped by the heart and it is a primary way to measure overall cardiac performance. The average cardiac output when using an the average stroke volume of 70 mL is 5.25 L/min, but the cardiac output can range from 5 to 6 L/min for a healthy adult at rest [15]. This performance requirement depends on both the heart rate and stroke volume because to calculate cardiac output the stroke volume and heart rate are multiplied together. The cardiac output essentially connects the heart rate to overall cardiovascular performance and acts as a minimum performance requirement for the system. Even if the heart rate is in the ideal range, the system won’t perform well unless blood flow is normal so a controller would need to regulate heart rate to allow the system to supply enough blood flow when disturbances occur. 

Overall, these performance requirements help to identify what healthy heart behavior looks like for the cardiovascular system and serves as a guide for how the controller should regulate heart rate. They determine our desired steady state value, how the system should respond to disturbances, and how certain changes in the body can affect the gain of a heart. These requirements give us a baseline for designing and evaluating a closed loop system with a controller and allows the model to mathematically and realistically behave well.

<Cardiovascular Disease>
<br>Cardiovascular disease is a group of diseases affecting human heart and blood vessels. There are many types:
<br> - Valve disease: tightening or leaking in your heart valves
<br> - Coronary artery disease: heart blood vessel blockage
<br> - Cerebrovascular disease: a disease of the blood vessels supplying the brain
<br> - Peripheral arterial disease: failure in supplying the arms and legs
<br> - Arrhythmia: irregular heart rhythms
<br> - Heart failure: problem with heart pumping/relaxing functions
Such symptoms of heart issues can cause chest pain (angina), shortness of breath (dyspnea), dizziness or fainting, or pressure on the chest. On top of such symptoms due to heart issues, blockages in blood vessels can lead to pain or cramps in your legs in motion, change of color on different body parts, swelling, or numbness.

Based on the research, we decided to explore arrhythmia deeper, defining ideal/regular heart beat as a reference input. Arrhythmia can be categorized in three parts: fast heartbeat (tachycardia), slow heartbeat (bradycardia), and premature heartbeats. 

The heart has a total of four chambers, two on each side, and four valves, which open and close to let blood flow only in one way when heart contracts and beats. Blood flows through the valve only when the valves open due to a pressure difference across the valves. Given that all four chambers beat in an orderly manner, the heart supplies blood to the lungs and to the rest of the body tissues.

![Shaded rendering of earlier version]({{ "/assets/images/heart anatomy.png" | relative_url }}){: .inline-image-c style="width: 500px"}

Figure 5: Heart valve anatomy

A proper electrical sequence of heartbeat begins in the right atrium (upper chamber) and spreads throughout the atria. The electrical impulses by the heartbeat travel down to the lower chambers (ventricles) to contract and beat in a regular manner. However, when the impulses are blocked in a system that disrupts the blood flow, the electrical activity becomes inconsistent, causing the heart to beat irregularly.

Various reasons can cause the disease, and one of the common causes is atrial fibrillation, where the heart's upper chamber beats irregularly and out of sync with the lower heart chambers. When an insufficient amount of the blood is pumped out of the atria, a blood pool is created, eventually forming a blood clot that affects the blood flow.

Defining such irregular heart beats as resulting in a nonzero “error” in a system, we established a system that treats ideal heart beat as a set reference input and an irregular heart beat as an output. Caused by changes in the electrical signals that control the human heartbeat, arrhythmia can be resolved by an Implantable Cardiac Defibrillator (ICD) under the skin, which we will discover more later on.


<ICD: Medical Remedy>
<br>An ICD is an implantable device implanted under the patient’s skin that seeks to detect and correct dangerously fast and irregular heartbeats known as arrhythmias. The device does this by monitoring heart rate through the electrical impulses of heartbeats, and delivering an electrical shock to the heart, ultimately resetting the heart’s electrical system to a normal rhythm. 

ICDs monitor the heart’s electrical activity through wire leads that are connected directly to the heart’s chambers. These leads deliver signals to the ICD, which generates and sends an electrical signal back to the heart in the event of an arrhythmia. 

![Shaded rendering of earlier version]({{ "/assets/images/ICD.png" | relative_url }}){: .inline-image-c style="width: 500px"}

Figure 6. Diagram of an ICD [9].

The ICD’s function can be modeled as a device that takes the heart rate error as an input:
<br>e=r-y
<br>where r is the reference, ideal heart rate, and y is the heart’s current heart rate, detected through the wire leads. 

This error is then processed through the ICD’s controller, which will alert of an arrhythmia event if the value of the error is high enough within the threshold of irregular heartbeating. When this happens, the ICD will generate a large electrical shock, which is modeled as an impulse input function: 
f(t)=F0(t)
A PID controller is best suited to satisfy the ICD’s goals. One reason for this is accuracy—a PID controller will drive the steady state error to zero. This is essential for the heart’s function because a nonzero steady state error would mean that the patient’s heart rate wouldn’t return to a regular rhythm, which can cause further complications. Additionally, the PID controller will constantly be readjusting and monitoring the system based on the error to provide more accurate results for impulse. 

In fact, ICDs are commonly described to have a “fuzzy” PID controller, which means that the numerical values for the PID gains (KP, KI, and KD) are changed and adapted in real-time, ultimately enhancing accuracy and improving performance [11].



References
<br>[1] C. C. medical professional, “How blood flows through your heart & body,” Cleveland Clinic, https://my.clevelandclinic.org/health/articles/17060-how-does-the-blood-flow-through-your-heart. [Accessed Dec. 6, 2025]. 
[2] Figure 2: Block diagram of heart, https://www.researchgate.net/figure/Block-Diagram-of-Heart_fig2_373465786. [Accessed Dec. 6, 2025]. 
[3] W. N. J. BE;, “The arterial windkessel,” Medical & biological engineering & computing, https://pubmed.ncbi.nlm.nih.gov/18543011/. [Accessed Dec. 6, 2025]. 
[4] M. DiDomizio, G. D’Elia, and S. Klein, rep.
[5] “Fit an ordinary differential equation (ODE),” MATLAB & Simulink, https://www.mathworks.com/help/optim/ug/fit-differential-equation-ode.html. [Accessed Dec. 6, 2025].
[6] Cleveland Clinic, “Cardiovascular Disease,” Cleveland Clinic, 2024. [Online]. Available: https://my.clevelandclinic.org/health/diseases/21493-cardiovascular-disease. [Accessed: Dec. 7, 2025].
[7] World Health Organization, “Cardiovascular diseases (CVDs),” WHO, 2025. [Online]. Available: https://www.who.int/news-room/fact-sheets/detail/cardiovascular-diseases-(cvds). [Accessed: Dec. 7, 2025].
[8] American Heart Association, “About Arrhythmia,” American Heart Association, 2025. [Online]. Available: https://www.heart.org/en/health-topics/arrhythmia/about-arrhythmia. [Accessed: Dec. 7, 2025].
[9] Mayo Clinic Staff, “Implantable cardioverter-defibrillators (ICDs),” Mayo Clinic, February, 2025. Available: https://www.mayoclinic.org/tests-procedures/implantable-cardioverter-defibrillators/about/pac-20384692. [Accessed Dec. 10, 2025].
[10] W. Shi, “Advanced intelligent control and optimization for cardiac pacemaker systems,” NJIT Digital Commons, May 2012. Available: https://digitalcommons.njit.edu/cgi/viewcontent.cgi?article=1361&context=dissertations#:~:text=Thus%2C%20this%20work%20develops%20a,pulse%20amplitude%20for%20successful%20entrainment. [Accessed Dec. 10, 2025].
[11] S. J. Abbasi, W. J. Kim, J. Kim, M. C. Lee, B. J. Lee, and M. J. Shin, “Robust Control Design of a Human Heart Rate System for Cardiac Rehabilitation Exercise," Electronics, vol. 11, no. 24, December, 2022. [4081]. Available: https://www.mdpi.com/2079-9292/11/24/4081. [Accessed Dec. 5, 2025].
[12] American Heart Association, “Target heart rates chart,” American Heart Association, 2025. [Online]. Available: https://www.heart.org/en/healthy-living/fitness/fitness-basics/target-heart-rates. [Accessed Dec. 10, 2025].
[13] American Heart Association, “High Blood Pressure,” American Heart Association, 2025. [Online]. Available: https://www.heart.org/en/health-topics/high-blood-pressure. [Accessed Dec. 10, 2025].
[14] M. L. Chuang and R. M. Peshock, “Normal Cardiac Anatomy: Stroke Volume,” in Cardiovascular Magnetic Resonance, 3rd ed. 2019. [Online]. Available: https://www.sciencedirect.com/topics/nursing-and-health-professions/heart-stroke-volume. [Accessed Dec. 10, 2025].
[15] Cleveland Clinic, “Cardiac Output,” Cleveland Clinic, 2022. [Online]. Available: https://my.clevelandclinic.org/health/diagnostics/23344-cardiac-output. [Accessed Dec. 10, 2025].

Appendix
%3260 Final Project: Heart Rate ODE

data = readmatrix('C1.pre','FileType','text','Delimiter',' ');

t = data(:,1);   % time (sec)
HR = data(:,2);  % heart rate (bpm)
t_center = t - 15552.672;
t_min = t_center/60;
plot(t_min, HR, 'b'); xlabel('Time (min)'); ylabel('HR (bpm)');
grid on;
title('Heart Rate (BPM) over Time')


%zoomed in section
zoom_start = 0; % Adjust this value as needed for the desired start time in minutes
zoom_end = zoom_start + 300/60; % 10 seconds in minutes

% Find the indices for the zoomed-in time range
zoom_indices = (t_min >= zoom_start) & (t_min <= zoom_end);
t_zoom =t_min(zoom_indices);
HR_zoom = HR(zoom_indices);

% Plot the zoomed-in section of the data
figure;
plot(t_zoom, HR_zoom, 'b'); 
xlabel('Time (min)'); 
ylabel('HR (bpm)');
grid on;
title('Zoomed-In Heart Rate (BPM) over Time');

%%% 2nd order ODE fitting 
% Convert time to seconds for stability
t_zoom_sec = t_zoom * 60;
HR_zoom = HR_zoom(:);   % ensure column vector

% ODE solver function for given parameters
ode_fun = @(t, H, p) [ ...
    H(2);                   % H' 
    -p(1)*H(2) - p(2)*H(1) + p(3)   % H'' = -aH' - bH + c
];

% Wrapper that simulates ODE and returns solution at data times
model = @(p, tdata)local_ode_model(p, tdata, ode_fun);

% Initial guess: [a, b, c, H0, dH0]
p0 = [0.1, 0.1, 0, HR_zoom(1), 0];

% Fit ODE
opts = optimoptions('lsqcurvefit','Display','iter','MaxFunctionEvaluations',5000);
p_fit = lsqcurvefit(model, p0, t_zoom_sec, HR_zoom, [], [], opts);

a = p_fit(1); b = p_fit(2); c = p_fit(3);
H0 = p_fit(4); dH0 = p_fit(5);

fprintf("Fitted second-order ODE:\n");
fprintf("H'' + %.5f H' + %.5f H = %.5f\n", a, b, c);
fprintf("Initial conditions:  H(0)=%.2f,  H'(0)=%.4f\n", H0, dH0);

function H_model = local_ode_model(p, tdata, ode_fun)

    % initial conditions
    H0 = p(4);
    dH0 = p(5);
    y0 = [H0; dH0];

    % solve ODE
    [t_sol, H_sol] = ode45(@(t,H) ode_fun(t,H,p), tdata, y0);

    % Extract HR(t)
    H_model = H_sol(:,1);
end

%Time vector for ODE
t_fit = linspace(min(t_zoom_sec), max(t_zoom_sec), 100);
HR_fit = model(p_fit, t_fit);

% Plot the fitted model against the original data
figure;
plot(t_zoom_sec, HR_zoom, 'b', t_fit, HR_fit, 'r--');
xlabel('Time (sec)');
ylabel('HR (bpm)');
legend('Observed Data', 'Fitted Model');
grid on;
title('Fitted Second-Order ODE Model vs Observed Heart Rate');





