# Code
Code for article
function weighted Productivity(fileinput)

if ~exist(fileinput,'file')
    error('xls does not exist in search path of MATLAB');
end

[~,Inventor]=xlsread(fileinput,'sheet1','A2:A15355');
[Year]=xlsread(fileinput,'sheet1','B2:B15355');
[Num]=xlsread(fileinput,'sheet1','C2:C15355');

n=1;

A{1,1}=Inventor{1};
A{1,2}=1/(2016-Year(1)+1)*Num(1);

for i=2:length(Inventor)
    if strcmp(A{n,1},Inventor{i})
       A{n,2} = A{n,2}+1/(2016-Year(i)+1)*Num(i);
    else
       n=n+1;
       A{n,1}=Inventor{i};
       A{n,2}=1/(2016-Year(i)+1)*Num(i);         
    end
end

xlswrite('Problem1.xls',A);
