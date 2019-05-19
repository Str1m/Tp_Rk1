# Рубежный контроль №2
Сабитов Егор ИУ8-25

## QUEUE  
[SpawnTree](https://github.com/SpawnTree/Algorithms-Unlocked/blob/932618003a3431863905eb78cd42b5fd09a01c52/Source%20Files/Data%20Structures/FastGraphStructure.cpp "Ссылка на код")  
108 - метод push()   
109 - метод front()    
112 - метод empty()   
117 - метод pop()   
## SET  
[grumble](https://github.com/rogerclark/grumble/blob/ef5e7210a73d84655e979f1eb8a9461503e8d2bf/source/grumble/common/boost/boost/graph/detail/set_adaptor.hpp#L15 "Ссылка на код")  
15 - методы find(), end()  
32 - метод begin()  
47 - метод clear()  
52 - метод empty()  
57 - метод insert()  
## VECTOR
[rpi-rgb-led-matrix](https://github.com/hzeller/rpi-rgb-led-matrix/blob/ef550e49b91a36fae616ba8879e467e04da9552f/utils/led-image-viewer.cc "Ссылка на код")  
132 - метод size()  
140 - метод begin(), end()  
142 - метод push_back()  
Вектора в данном проектe используются для хранения "кадров". Весь проект направлен на работу с изображениями (приложение для просмотра изображений).
## TREE  
[lab-06-sorting-Str1m](https://github.com/bmstu-iu8-25-cpp-2019/lab-06-sorting-Str1m/blob/lab/include/sorting.hpp "Ссылка на код") (приватный репозиторий)
```cpp
template <class It, class Compare = std::less<>>
void add(It it1, std::vector<typename std::iterator_traits<It>::value_type>& v1,
        size_t n, Compare cmp = Compare{}) {
  auto buf1 = *it1;
  v1.resize(n);
  v1.push_back(buf1);
  size_t ind = v1.size() - 1;
  while (ind / 2 != 0) {
    if (cmp(v1[ind / 2], v1[ind])) {
      auto buf = v1[ind / 2];
      v1[ind / 2] = v1[ind];
     v1[ind] = buf;
      ind /= 2;
    } else {
      break;
    }
  }
}

template <class Compare = std::less<>, class T>
T del(std::vector<T>& v1, Compare cmp = Compare{}) {
  auto buf_val = v1[1];
  v1[1] = v1[v1.size() - 1];
  v1.resize(v1.size() - 1);
  size_t buf = 1;
  while (buf * 2 < v1.size()) {
    if (buf * 2 + 1 < v1.size()) {
      if (cmp(v1[buf * 2 + 1], v1[buf * 2])) {
        if (cmp(v1[buf], v1[buf * 2])) {
          auto b = v1[buf];
          v1[buf] = v1[buf * 2];
          v1[buf * 2] = b;
          buf *= 2;
        } else {
          break;
        }
      } else {
        if (cmp(v1[buf], v1[buf * 2 + 1])) {
          auto b = v1[buf];
          v1[buf] = v1[buf * 2 + 1];
          v1[buf * 2 + 1] = b;
          buf *= 2;
          buf++;
        } else {
          break;
        }
      }
    } else {
      if (cmp(v1[buf], v1[buf * 2])) {
        auto b = v1[buf];
        v1[buf] = v1[buf * 2];
        v1[buf * 2] = b;
        buf *= 2;
      } else {
        break;
      }
    }
  }
  return buf_val;
}

template <class It, class Compare = std::less<>>
void heap_sort(It first, It last, Compare cmp = Compare{}) {
  std::vector<typename std::iterator_traits<It>::value_type> v1;
  v1.push_back(0);
  size_t n = 1;
  auto f1 = first;
  while (f1 != last) {
    add(f1, v1, n, cmp);
    f1++;
    n++;
  }
  f1--;
  while (f1 >= first) {
    *f1 = del(v1, cmp);
    f1--;
  }
}
```
В функции heap_sort используется работа с деревом, с помощью методов добавления (add) и удаление (del) само дерево реализовано через вектор и в ходе работы с ним сортируется в нужном порядке. 
