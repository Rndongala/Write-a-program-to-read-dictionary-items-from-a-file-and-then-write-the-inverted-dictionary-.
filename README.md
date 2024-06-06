Write a program to read dictionary items from a file and then write the inverted dictionary to a file. Ensure the program includes the following components: 

1.The input file for your original dictionary (with at least six items). 
2. The Python program you used to read from a file, invert the dictionary, and write to a different file. (You need to create a dictionary file and invert it into another file). 
3. The output file for your inverted dictionary. 
Sample Input File (Not specific) 
{ 
apple: red 
banana: yellow 
cherry: red 
mango: yellow 
grapes: black, green 

} 
Sample Output File: 
{ 
red: apple, cherry 
yellow: banana, mango 
black: grapes 
blue: grapes 
}

Programming Instructions:
The code and its output must be explained technically. The explanation can be provided before or after the code, or in the form of comments within the code.
# Sample input dictionary stored in a file
input_file = 'original_dict.txt'
output_file = 'inverted_dict.txt'

# Create the input file with the dictionary
original_dict = {
    'apple': 'red',
    'banana': 'yellow',
    'cherry': 'red',
    'mango': 'yellow',
    'grapes': 'black, green'
}

with open(input_file, 'w') as f:
    f.write(str(original_dict))

# Python program to read the dictionary, invert it, and write the inverted dictionary to another file
def invert_dictionary(input_filepath, output_filepath):
    # Read the original dictionary from the input file
    with open(input_filepath, 'r') as f:
        content = f.read()
        original_dict = eval(content)

    # Invert the dictionary
    inverted_dict = {}
    for key, value in original_dict.items():
        # Handle multiple values split by commas
        values = [v.strip() for v in value.split(',')]
        for val in values:
            if val not in inverted_dict:
                inverted_dict[val] = []
            inverted_dict[val].append(key)

    # Write the inverted dictionary to the output file
    with open(output_filepath, 'w') as f:
        f.write(str(inverted_dict))

# Execute the function
invert_dictionary(input_file, output_file)

# Reading the output file to display the result
with open(output_file, 'r') as f:
    inverted_content = f.read()
    print("Inverted Dictionary:\n", inverted_content)
