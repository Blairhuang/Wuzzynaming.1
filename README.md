# Wuzzynaming.1



#WuzzyNaming test

#----------User Input Interface----------------------------------
print('do you want to build your custom corpus or use Build_in corpus?')
build=input('')

print('if yes, input your file directory(make sheet1 as the roomname')
directory = input('')
#directory = r'C:\Users\DELL\Desktop\RoomName' #(directory of the FolderPath of RoomName excel documents)

print('input the directory of your important nouns:')
imp_directory = input('')
#imp_directory = r'C:\Users\DELL\Desktop\wuzzynaming\important_nouns\Important_Noun.xlsx'(directory of the FilePath of important_noun excel file)

print('do you need translate? yes or no')
translate = input('')
#translate='no' or 'yes'
print('input ROOM function: ')
input_function=input('')
#input_function='wc'
print('input ROOM description: ')
input_description=input('')
#input_description='inside'
print('input ROOM ownership: ')
input_ownership=input('')
print('input ROOM sector: ')
input_sector = input('')
#input_sector = 'stadium'
print('input similarity tolerance: ')
tolerance=float(input(''))
#tolerance =0.88

#----------Standard Process----------------------------------
combined_dict = standard_Dict(build.lower(),imp_directory,directory,0.88) #(you can input the tolerance on your own)
#imp_directory = important file directory 

Export = Custom_or_Build(build.lower(),directory,r'C:/Users/DELL/Desktop/wuzzynaming/RoomCorpus/Corpus_Combo.txt',r'C:/Users/DELL/Desktop/wuzzynaming/RoomCorpus/All_corpus.txt')
#(for corpus, replace the FilePath with your own path)
#eg. Export = Custom_or_Build(build.lower(),directory,r'.../Corpus_Combo.txt',r'.../All_corpus.txt')

All_corpus = Export[1]
noun_lst = Export[2]


FUNCTION = SpellCorrection(translate,input_function,All_corpus)
DESCRIPTION = SpellCorrection(translate,input_description,descript_corpus())
#SECTOR = Archi_Sector(input_sector,translate)
SECTOR = 'Stadium'


#----------Standard Result----------------------------------
print(standard(FUNCTION,DESCRIPTION,SECTOR,input_ownership,combined_dict)) #present function,description,sector,ownership, property 

#----------Function_Synonym Result----------------------------------
Function_synonym= Synonym_Function(FUNCTION,noun_lst,tolerance) 
print(Function_synonym)


##Find the system to eveluate the result 


#input change_room 


