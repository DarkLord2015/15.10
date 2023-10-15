              # 15.10
              Андреев Хабибулина ИП-11
              using System;
              using System.Collections.Generic;
              using System.Linq;
              using System.Text;
              using System.Threading.Tasks;
              
              namespace CorrectCodeLibrary
              {
                  public class CorrectCodeClass
                  {
                      /// <summary>
                      /// Метод принимает в качестве параметра строку. 
                      /// </summary>
                      /// <param name="candidate">Код</param>
                      /// <returns>
                      /// Метод возвращает true, если входная строка соответствует следующим условиям: строка имеет правильную длину; десятый символ строки(контрольное значение) содержит правильную цифру. При нарушении данных условий, метод возвращает false.
                      /// </returns>
                      public static bool IsCorrectCode(string candidate)
                      {
                          if (candidate.Length != 10) return false;
                          char[] array = candidate.ToCharArray();
                          int last = (int)Char.GetNumericValue(array[9]);
                          int zv = 0;
                          for (int i = 0; i < 9; i++)
                          {
                              zv += (int)Char.GetNumericValue(array[i]);
                          }
                          if (zv % 10 == 0)
                          {
                              if (last != 0) return false;
                          }
                          else
                          {
                              if (zv % 3 == 0)
                              {
                                  if (last != 1) return false;
                              }
                              else
                              {
                                  if (last != 9) return false;
                              }
                          }
                          return true;
                      }
                  }
              }



              TEsts




                using Microsoft.VisualStudio.TestTools.UnitTesting;
                using System;
                using CorrectCodeLibrary;
                
                namespace CorrectCodeTests
                {
                    [TestClass]
                    public class CorrectCodeTests
                    {
                        /// <summary>
                        /// Ввод пустой строки
                        /// </summary>
                        [TestMethod]
                        public void UnCorrectCode1()
                        {
                            //Act
                            string candidate = "";
                            //Arrange
                            bool actual = CorrectCodeClass.IsCorrectCode(candidate);
                            //Assert
                            Assert.IsFalse(actual);
                        }
                        /// <summary>
                        /// Ввод короткой строки
                        /// </summary>
                        [TestMethod]
                        public void UnCorrectCode2()
                        {
                            //Act
                            string candidate = "123";
                            //Arrange
                            bool actual = CorrectCodeClass.IsCorrectCode(candidate);
                            //Assert
                            Assert.IsFalse(actual);
                        }
                        /// <summary>
                        /// Ввод длинной строки
                        /// </summary>
                        [TestMethod]
                        public void UnCorrectCode3()
                        {
                            //Act
                            string candidate = "123123123123123";
                            //Arrange
                            bool actual = CorrectCodeClass.IsCorrectCode(candidate);
                            //Assert
                            Assert.IsFalse(actual);
                        }
                        /// <summary>
                        /// Проверка на буквы
                        /// </summary>
                        [TestMethod]
                        public void UnCorrectCode14()
                        {
                            //Act
                            string candidate = "strokasymbfafafa";
                            //Arrange
                            bool actual = CorrectCodeClass.IsCorrectCode(candidate);
                            //Assert
                            Assert.IsFalse(actual);
                        }
                        /// <summary>
                        /// Неккоректный код
                        /// </summary>
                        [TestMethod]
                        public void UnCorrectCode5()
                        {
                            //Act
                            string candidate = "1234123401";
                            //Arrange
                            bool actual = CorrectCodeClass.IsCorrectCode(candidate);
                            //Assert
                            Assert.IsFalse(actual);
                        }
                        /// <summary>
                        /// Неккоректный код с 4 на конце
                        /// </summary>
                        [TestMethod]
                        public void UnCorrectCode6()
                        {
                            //Act
                            string candidate = "1234123404";
                            //Arrange
                            bool actual = CorrectCodeClass.IsCorrectCode(candidate);
                            //Assert
                            Assert.IsFalse(actual);
                        }
                        /// <summary>
                        /// Корректный код с 0 на конце
                        /// </summary>
                        [TestMethod]
                        public void UnCorrectCode7()
                        {
                            //Act
                            string candidate = "1234123400";
                            //Arrange
                            bool actual = CorrectCodeClass.IsCorrectCode(candidate);
                            //Assert
                            Assert.IsTrue(actual);
                        }
                        /// <summary>
                        /// Корректный код с 9 на конце
                        /// </summary>
                        [TestMethod]
                        public void UnCorrectCode8()
                        {
                            //Act
                            string candidate = "3000030001";
                            //Arrange
                            bool actual = CorrectCodeClass.IsCorrectCode(candidate);
                            //Assert
                            Assert.IsTrue(actual);
                        }
                        /// <summary>
                        /// Корректный код с 9 на конце
                        /// </summary>
                        [TestMethod]
                        public void UnCorrectCode9()
                        {
                            //Act
                            string candidate = "3000130009";
                            //Arrange
                            bool actual = CorrectCodeClass.IsCorrectCode(candidate);
                            //Assert
                            Assert.IsTrue(actual);
                        }
                    }
                }

