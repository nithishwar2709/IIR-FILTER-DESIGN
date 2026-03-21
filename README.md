# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc ; 
close ; 

wp = input('Enter the pass band frequency (Radians )= ' ); 
ws = input('Enter the stop band frequency (Radians )= ' ); 
alphap = input( 'Enter the pass band attenuation (dB)=' ); 
alphas = input('Enter the stop band attenuation(dB)=');
T = input('Enter the Value of sampling Time=')

omegap = (2/T)*tan(wp/2);
disp(omegap,'omegap=');
omegas = (2/T)*tan(ws/2);
disp(omegas,'omegas=');

N = log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap));
disp(N,'N=');
N = ceil(N);
disp(N,'Round off value of N');

omegac = omegap/(((10^(0.1*alphap))-1)^(1/(2*N)));
disp(omegac,'omegac=');

disp('Normalised Analog LPF Transfer function H(S)=');
hs_Normalised = analpf(N,'butt',[0,0],1);
disp(hs_Normalised);

disp('Analog LPF Transfer function H(S)=');
hs=analpf(N,'butt',[0,0],omegac);
disp(hs);

z = poly(0,'z');
Hz = horner(hs,(2/T)*((z-1)/(z+1)))
disp('Digital LPF Transfer function H(Z)=');
disp(Hz);

HW = frmag(Hz,512);
w = 0:%pi/511:%pi;
plot(w/%pi,abs(HW));
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of Butterworth IIR LPF')
```
# MANUAL CALCULATION:
![WhatsApp Image 2026-03-21 at 3 23 22 PM](https://github.com/user-attachments/assets/1e77e70d-f58a-4ddf-bc8e-98234ffff5fa)
![WhatsApp Image 2026-03-21 at 3 23 19 PM](https://github.com/user-attachments/assets/a6bbc95e-a812-467d-8593-90bcbad57f62)
![WhatsApp Image 2026-03-21 at 3 23 19 PM (1)](https://github.com/user-attachments/assets/0f6b9b3a-9c10-4806-b0c2-695712606c2c)



# OUTPUT: 
<img width="1919" height="1199" alt="Screenshot 2026-02-23 084839" src="https://github.com/user-attachments/assets/bbe83b92-27c1-4226-830a-858cee5d809e" />

# RESULT: 
Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was 
verified.

# EXP 3 B: DESIGN OF LOW PASS CHEBYSHEV IIR FILTER USING BILINEAR TRANSFORMATION

# AIM: 

# To a design of low pass Chebyshev IIR filter using Bilinear Transformation.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc;
close;

wp = input('Enter the pass band frequency (Radians)=')
ws = input('Enter the stop bande frequency (Radians)=')
alphap = input('Enter the pass band attenuation (dB)=')
alphas = input('Enter the stop band attenuation (dB)=')
T = input('Enter the Value of sampling Time=')

omegap = (2/T)*tan(wp/2);
disp(omegap,'omegap=');
omegas = (2/T)*tan(ws/2);
disp(omegas,'omegas=');

N = acosh(sqrt(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1)))/(acosh(omegas/omegap));
disp(N,'N=');
N = ceil(N);
disp(N,'Round off value of N=');

omegac = omegap/(((10^(0.1*alphap))-1)^(1/(2*N)));
disp(omegac,'omegac=');

Epsilon = sqrt ((10^(0.1*alphap))-1);
disp(Epsilon,'Epsilon=');

[pols,gn] = zpch1(N,Epsilon,omegap);
disp(gn,'Gain');
disp(pols,'Poles');

hs = poly(gn,'s','coeff')/real(poly(pols,'s'));
disp(hs,'Analog Low pass Chebyshev Filter Transfer function'); 
 
z=poly(0,'z');
 
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))
disp(Hz,'Digital LPF Transfer function H(Z)='); 
 
HW=frmag(Hz,512);
 
w=0:%pi/511:%pi ; 
plot(w/%pi,abs(HW)); 
xlabel(' Normalized Digital Frequency w'); 
ylabel('Magnitude '); 
title(' Frequency Response of Chebyshev IIR LPF');

```
# MANUAL CALCULATION:

![WhatsApp Image 2026-03-21 at 3 27 24 PM](https://github.com/user-attachments/assets/0ee27595-fe88-41b5-b5cb-36f125735a71)
![WhatsApp Image 2026-03-21 at 3 27 23 PM (1)](https://github.com/user-attachments/assets/3a56e375-e993-4775-a860-c8c9521bbbf2)
![WhatsApp Image 2026-03-21 at 3 27 23 PM](https://github.com/user-attachments/assets/af41f88d-db6c-4469-8871-937482e4fc7a)



# OUTPUT: 

<img width="1912" height="1195" alt="Screenshot 2026-02-23 093023" src="https://github.com/user-attachments/assets/fe623ea9-f95b-405c-b9bd-cfeba9bfec78" />


# RESULT: 
Thus design of Chebyshev Low pass IIR filter waveforms were plotted and output was 
verified. 

