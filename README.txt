<?php


class JapaneseСrossword
{
    function answerMax($rows, $columns)
    {
        $result = [
            [0, 0, 0, 0, 0],
            [0, 0, 0, 0, 0],
            [0, 0, 0, 0, 0],
            [0, 0, 0, 0, 0],
            [0, 0, 0, 0, 0],
        ];

        result1($result, $rows,$columns);

        result1X($result, $rows,$columns);

        resultX1($result, $rows,$columns);

        for ($i = 0; $i < count($result); $i++) {                                                         //echo $rows[$i];
            if (summaRows01($result, $i) == array_sum($rows[$i])) {                                //echo 'if1 OK'.$this->summaRows01($result, $i).'='.array_sum($rows[$i]).'<br>';
                for ($x = 0; $x < count($result); $x++) {
                    if ($result[$i][$x] !== 'x') {
                        $result[$i][$x] = 1;
                    } else {
                    }
                }
            }
        }

        for ($i = 0; $i < count($result); $i++) {
            if (summaColumns01($result, $i) == array_sum($columns[$i])){
                for ($x = 0; $x < count($result); $x++) {
                    if ($result[$x][$i] !== 'x') {
                        $result[$x][$i] = 1;
                    } else {
                    }
                }
            }
        }

        for ($r = 0; $r < count($result); $r++) {
            if (array_sum($result[$r]) == array_sum($rows[$r])) {
                for ($x = 0; $x < count($result[$r]); $x++) {
                    if ($result[$r][$x] != 1) {
                        $result[$r][$x] = 'x';
                    } else {
                    }
                }
            } else {
            }
        }

        for ($i = 0; $i < count($result); $i++) {                                                         //count($result)=6
            if (summaColumns1($result, $i) == array_sum($columns[$i])) {
                for ($x = 0; $x < count($result); $x++) {
                    if ($result[$x][$i] != 1) {
                        $result[$x][$i] = 'x';
                    } else {
                    }
                }
            } else {
            }
        }

        for ($i = 0; $i < count($result); $i++) {                                                         //echo $rows[$i];
            if (summaRows01($result, $i) == array_sum($rows[$i])) {                                //echo 'if1 OK'.$this->summaRows01($result, $i).'='.array_sum($rows[$i]).'<br>';
                for ($x = 0; $x < count($result); $x++) {
                    if ($result[$i][$x] !== 'x') {
                        $result[$i][$x] = 1;
                    } else {
                    }
                }
            }
        }

        for ($i = 0; $i < count($result); $i++) {
            if (summaColumns01($result, $i) == array_sum($columns[$i])){
                for ($x = 0; $x < count($result); $x++) {
                    if ($result[$x][$i] !== 'x') {
                        $result[$x][$i] = 1;
                    } else {
                    }
                }
            }
        }

        for ($i = 0; $i < count($result); $i++) {
            for ($b = 0; $b < count($result); $b++)
                echo $result[$i][$b];
            if ($b == count($result)) {
                echo "<br>";
            }
        }
    }


}

function summaColumns1($result, $columns)
{
    $sumResult = 0;
    for ($b = 0; $b < count($result); $b++) {
        if ($result[$b][$columns] == 1) {
            $sumResult++;
        }
    }
    return $sumResult;
}

function summaColumns01($result, $columns)
{
    $sumResult = 0;
    for ($b = 0; $b < count($result); $b++) {
        if ($result[$b][$columns] !== 'x') {
            $sumResult++;
        }
    }
    return $sumResult;
}

function summaRows01($result, $rows)
{
    $sumResult = 0;
    for ($b = 0; $b < count($result); $b++) {
        if ($result[$rows][$b] !== 'x') {
            $sumResult++;
        }
    }
    //echo $sumResult;
    return $sumResult;
}

function result1 ($result, $rows, $columns){
    for ($i = 0; $i < count($rows); $i++) {
        for ($b = 0; $b < count($rows[$i]); $b++) {
            if (($intersect = count($result) - $rows[$i][$b]) < (count($result) / 2)) {
                for ($c = 0; $c < count($rows); $c++) {
                    if ($c > ($intersect - 1) && $c < (count($rows) - $intersect)) {
                        $result[$i][$c] = 1;
                    }
                }
            }
        }
    }

    for ($i = 0; $i < count($columns); $i++) {
        for ($b = 0; $b < count($columns[$i]); $b++) {
            if (($intersect = count($result) - $columns[$i][$b]) < (count($result) / 2)) {
                for ($c = 0; $c < count($columns); $c++) {
                    if ($c > ($intersect - 1) && $c < (count($columns) - $intersect)) {
                        $result[$c][$i] = 1;
                    }
                }
            }
        }
    }
    return $result;
}

function result1X ($result, $rows, $columns){
    for ($r = 0; $r < count($result); $r++) {
        if (array_sum($result[$r]) == array_sum($rows[$r])) {
            for ($x = 0; $x < count($result[$r]); $x++) {
                if ($result[$r][$x] != 1) {
                    $result[$r][$x] = 'x';
                } else {
                }
            }
        } else {
        }
    }

    for ($i = 0; $i < count($result); $i++) {                                                         //count($result)=6
        if (summaColumns1($result, $i) == array_sum($columns[$i])) {
            for ($x = 0; $x < count($result); $x++) {
                if ($result[$x][$i] != 1) {
                    $result[$x][$i] = 'x';
                } else {
                }
            }
        } else {
        }
    }
    return $result;
}

function resultX1($result, $rows,$columns){
    for ($i = 0; $i < count($result); $i++) {                                                         //echo $rows[$i];
        if (summaRows01($result, $i) == array_sum($rows[$i])) {                                //echo 'if1 OK'.$this->summaRows01($result, $i).'='.array_sum($rows[$i]).'<br>';
            for ($x = 0; $x < count($result); $x++) {
                if ($result[$i][$x] !== 'x') {
                    $result[$i][$x] = 1;
                } else {
                }
            }
        }
    }

    for ($i = 0; $i < count($result); $i++) {
        if (summaColumns01($result, $i) == array_sum($columns[$i])){
            for ($x = 0; $x < count($result); $x++) {
                if ($result[$x][$i] !== 'x') {
                    $result[$x][$i] = 1;
                } else {
                }
            }
        }
    }
    return $result;
}

