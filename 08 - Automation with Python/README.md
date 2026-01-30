# Update a File Through a Python Algorithm

This project demonstrates how Python can be used to automate updates to an IP allow list at a health care organization. Access to restricted systems is controlled by employee IP addresses stored inside an ```"allow_list.txt"``` file. A separate remove list identifies IP addresses that must be revoked. I created an algorithm that reads the allow list, removes any IP address found in the remove list, and updates the file with the revised list. This automation strengthens access control procedures and reduces human error in security operations.

## Open the file that contains the allow list

To begin, I opened the ```"allow_list.txt"``` file. First, I assigned the file name as a string to the ```import_file``` variable:
```
import_file = "allow_list.txt"
```
Next, I used a ```with``` statement to open the file:
```
with open(import_file, "r") as file:
    ip_addresses = file.read()
```
The ```with``` statement is paired with the built-in ```open()``` function in read mode (```"r"```). Using ```with``` ensures that Python automatically closes the file after exiting the block. The two parameters inside ```open()``` specify the file name and the action to perform—in this case, reading the file. The ```as``` keyword assigns the opened file object to the variable ```file```, which I use to access the file’s contents.

## Read the file contents

To process the allow list, I used the ```.read()``` method to convert the file contents into a single string:
```
ip_addresses = file.read()
```
The ```.read()``` method is only available when the file is opened in read mode (```"r"```). It returns the full contents of the file as a string, which allows me to later manipulate the IP addresses programmatically. Storing this string in the variable ```ip_addresses``` prepares it for further processing.

## Convert the string into a list

Because I need to remove individual IP addresses, the string must be converted into a list. To do this, I applied the ```.split()``` method:
```
ip_addresses_list = ip_addresses.split()
```
The ```.split()``` method converts a string into a list by separating it on whitespace by default. In this context, each IP address in the allow list is separated by a newline, so ```.split()``` cleanly produces a list of IP addresses. Storing this list in ```ip_addresses_list``` makes it easy to remove items programmatically.

## Iterate through the remove list

A key part of the algorithm is iterating through each IP address in the remove list. I did this using a ```for``` loop:
```
for element in remove_list:
```
A ```for``` loop in Python repeats a block of code for every item in a sequence. The loop variable ```element``` represents each IP address in the ```remove_list``` as the loop progresses. This structure lets me compare each element with the allow list and determine whether it needs to be removed.

## Remove IP addresses that are on the remove list

My algorithm must remove IP addresses from the allow list if they also appear in the remove list. Because the allow list contains no duplicates, I was able to use the following logic:
```
for element in remove_list:
    if element in ip_addresses_list:
        ip_addresses_list.remove(element)
```
First, I created a conditional ```if element in ip_addresses_list:``` to ensure that ```.remove()``` is only used on valid entries—otherwise, attempting to remove a non-existent item would cause an error. Inside this conditional, I applied the ```.remove()``` method to delete the element from the allow list. Passing the loop variable as the argument removes each matching IP address.

Applying ```.remove()``` this way works correctly because there are no duplicate IP addresses in the allow list.

## Update the file with the revised list of IP addresses

After removing all required IP addresses, I converted the list back into a string using the .join() method:
```
updated_ip_addresses = "\n".join(ip_addresses_list)
```
The ```.join()``` method joins all elements in an iterable using the string it is called on as the separator. By applying it to ```"\n"```, I ensure each IP address appears on its own line in the updated file.

Next, I used another ```with``` statement and the ```.write()``` method to update the allow list file:
```
with open(import_file, "w") as file:
    file.write(updated_ip_addresses)
```
This time, I used the ```"w"``` mode with ```open()```, which allows Python to overwrite the file’s existing contents. The ```.write()``` method replaces the original allow list with the updated one, ensuring former employees or unauthorized IP addresses can no longer access restricted systems.

## Summary

I created a Python algorithm that removes IP addresses found in a remove list from the ```"allow_list.txt"``` file. The algorithm begins by opening the allow list file and converting its contents into a string. It then converts this string into a list so individual IP addresses can be evaluated. Next, the algorithm iterates through the remove list and removes any matching IP addresses from the allow list. Afterward, it uses the ```.join()``` method to convert the updated list back into a string. Finally, it writes this updated string back to the file, ensuring the allow list reflects only authorized IP addresses.
