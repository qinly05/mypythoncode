import os
import os.path
import shutil

def cftf(src, dst, *tail):

        '''
        Collect all certain suffix files in one folder
        and return a iterable object

        src
            The path of source folder that contains all files.

        dst
            The path of destination folder.

        tail
            The suffix(s) of file(s).

        example:
        cftf(r'e:\test', r'e:\test2', 'txt', 'docx')
           
        '''

    if os.path.exists(src) is False:
        print('The directory', src, 'does not exist.')
        raise FileNotFoundError()
    
    def cactf():

        files_dir = os.walk(src)
        file_list = []
        tails = []
        for every_tail in tail:
            every_tail = '.'+every_tail
            tails.append(every_tail)
        for elem in files_dir:
            if elem[2]:
                for file in elem[2]:
                    name = os.path.splitext(file)
                    if name[1].lower() in tails:
                        file_list.append(os.path.join(elem[0],file))
        return iter(file_list)

    if os.path.exists(dst) is False:
        os.mkdir(dst)
    for file_dir in cactf():
        shutil.copy(file_dir, dst)

##example
##if __name__ == '__main__':
##    cftf(r'e:\test', r'e:\test2', 'txt')
