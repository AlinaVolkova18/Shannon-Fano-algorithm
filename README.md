Алгоритм Шеннона-Фано анализирует входные данные и на их основе строит бинарное дерево минимального кодирования. Используя это дерево, затем можно выполнить повторное считывание входных данных и закодировать их. Алгоритм использует коды переменной длины: часто встречающийся символ кодируется кодом меньшей длины, редко встречающийся — кодом большей длины. Коды Шеннона-Фано - префиксные, то есть никакое кодовое слово не является префиксом любого другого. Это свойство позволяет однозначно декодировать любую последовательность кодовых слов.
Кодер
На вход кодера поступает файл. Происходит посимвольное считывание файла, в ходе которого считается количество появлений каждого символа. В это же время создается алфавит, в который записывается по порядку символ и частота его встречаемости. Далее мы сортируем наш алфавит по убыванию частот. Код Шеннона-Фано строится с помощью дерева. Полученный после сортировки алфавит будет корнем дерева. Мы разделяем алфавит на две группы так, чтобы суммарные частоты символов были максимально близки друг к другу – то есть начинаем строить дерево от корня. Затем мы по такому же принципу разделяем каждую группу до тех пор, пока во всех группах не окажется ровно по одному символу. После построения дерева нам нужно дать каждому символу свой уникальный код. Чтобы добраться до какого-то определенного символа мы перемещаемся от корня дерева вправо или влево. Исходя из этого, если принять, что перемещение влево эквивалентно нулевому биту, а перемещение вправо – единичному, то у каждого символа появится свой неповторяющийся код.   
Декодер
Декодеру также на вход поступает файл, но уже закодированный. Мы по битам считываем файл и записываем количество повторений каждого бита. Создаем алфавит и сортируем по убыванию частот встречаемости. По такому же принципу строим дерево. Мы начинаем с корневого узла и выбираем из сжатого потока битов по одному биту. Если бит является нулевым, мы перемещаемся влево, если единичным – вправо. Мы будем объединять каждые 8 битов в байт, после чего выполнять запись в файл. 
