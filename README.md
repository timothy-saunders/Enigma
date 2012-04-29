Enigma
======

An attempt to code a matlab function that encrypts like the WW2 german Enigma machines


function [coded_message] = enigma(msg)
%Encodes a message based off the WW2 german enigma machine, type a message

%Turn the message into ascii code
numbered = double(msg);
wheel1 = [76, 80, 88, 70, 81, 68, 89, 83, 77, 78, 79, 65, 73, 74, 75, 66, 69, 87, 72, 87, 90, 84, 82, 67, 71, 85];
wheel1_base = wheel1;
%wheel1_end = fliplr(wheel1);

for a = 1:length(msg)
   %Match up the unencrypted value with its position in the alphabet
   posi = 90 - numbered(a);
   partial1(a) = wheel1(end - posi);
   
   for n = (1:(26-a));
       wheel1(n) = wheel1_base(n + a);
   end
   
   for z = 1:a
       wheel1(27 - z) = wheel1_base(z);
   end
   
end
final = char(partial1);
coded_message = final;