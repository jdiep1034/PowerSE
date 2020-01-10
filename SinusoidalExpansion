% Justin Diep
% 12-18-19
% Power Series Expansion of 12Cos(40t)

clear   % Clears variables in workspace
clf     % Clears figures
format shortG  % Format for meaningful output

%-----User Inputs-----
nUser = input('How many non-zero terms to sum for expansion of 12Cos(40t): ');
tUser = input('Please choose an ending time (ms): ');

%-----Creating Time Array-----
tmin = 0;   % Lower limit for time axis
tmax = tUser / 1000; % Upper limit for time axis
i = 400;     % Number of intervals
t = linspace(tmin,tmax,i+1); % t from 0 to 0.2 with 401 intervals
tms = t*1000;  % Convert t to ms

%-----Variables-----
p = 5;  % Phase of Project
a = 12;   % Amplitude
w = 40;   % Angular frequency

n = (0:2:nUser*2-2); % Array of values of n

an = a*w.^n.*(-1).^(n/2)./factorial(n); % Array of 6 non-zero coefficients
tab = table(n.',an.');  % Creates table with two columns from n and an
tab.Properties.VariableNames = {'n','an'}  % Names table variables

%-----(Inefficient Plotting)-----
%{
f1 = an(1)*t.^n(1);
f2 = f1 + an(2)*t.^n(2);
f3 = f2 + an(3)*t.^n(3);
f4 = f3 + an(4)*t.^n(4);
f5 = f4 + an(5)*t.^n(5);
f6 = f5 + an(6)*t.^n(6);
%}
%-----(Efficient Plotting)-----
subtotal = zeros(1,length(t));
hold on
for term = 1:(nUser)
    subtotal = subtotal + an(term)*t.^n(term);
    if term == nUser
        plot(tms,subtotal,'k','linewidth',2)
    else
        plot(tms,subtotal)
    end
end

%-----Plotting-----
ax = gca;
ax.FontSize = 15;
xlabel('time (ms)','Fontsize',16)
ylabel('f(t)','Fontsize',16)
axis([-inf tUser -a*1.15 a*1.15])
title({strcat('ECE 202, Project 1: Phase'," ",num2str(p)," ",num2str(a),'Cos(',num2str(w),'t)');...
    strcat('Approximated by First'," ",num2str(nUser)," ",'Non-zero Terms');...
    strcat('in Truncated Series for'," ",num2str(tUser)," ",'ms');},'Fontsize',18)
grid on
legend("Up to n = "+(n/2+1),'Fontsize',10,'Location','eastoutside')
