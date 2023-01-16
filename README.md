## area_converter.py
This function converts OSPF area ID from decimal to dotted decimal



def convert_area(area):
    """
    Convert decimal to binary. 
    Prepend 0's to binary.
    Split into 4 octets.
    Convert binary octets to dotted decimal format.
    """
    bin_area = bin(area)    # convert area to binary (0b... format)
    bin_area_list = list(bin_area)     # make list of bin values for example:  ['0', 'b', '1', '1', '0', '0', '1', '1', '0', '1', '0']
    bin_area_list.remove('b')          # remove 'b' from list
    while len(bin_area_list) < 32:     # prepend 0's to until 32 bits length
        bin_area_list.insert(0,'0')
    octet1 = ['0b'] + bin_area_list[:8]     # form the four octets in binary format
    octet2 = ['0b'] + bin_area_list[8:16]   
    octet3 = ['0b'] + bin_area_list[16:24]  
    octet4 = ['0b'] + bin_area_list[24:32]  
    octet1 = int(''.join(octet1), 2)       # joins the binary digits and converts to decimal format per octet
    octet2 = int(''.join(octet2), 2)
    octet3 = int(''.join(octet3), 2)
    octet4 = int(''.join(octet4), 2)
    converted_area = str(octet1) + '.' + str(octet2) + '.' + str(octet3) + '.' + str(octet4) # convert to str and print octet integers in dotted decimal.
    return converted_area
    # example input: 410 <-Decimal format
    # example output: 0.0.1.154 <-Dotted Decimal format
    # conversion website reference: https://www.beyondcli.com/ospf-conversion/
    # formula for conversion reference:  https://knowledgebase.paloaltonetworks.com/KCSArticleDetail?id=kA10g000000ClelCAC 

