gitѧϰ
 һ.�����汾��
    1������һ���յ�Ŀ¼
        mkdir learngit
        cd learngit
        pwd   ��ʾ��ǰĿ¼
    2��git init �����Ŀ¼���git���Թ���Ĳֿ�
		����ִ�к󣬵�ǰĿ¼���һ��.git��Ŀ¼����û����˵�����Ŀ¼Ĭ�������صģ�ʹ��ls -ah 
    3���ļ���ӵ��汾��
         ��learngit��������Ŀ¼�����һ���ļ� readme.txt 
		 ��һ���ļ��ŵ�Git�ֿ�ֻ��Ҫ������
		 ��һ����������git add����Git�����ļ���ӵ��ֿ⣺
		 $ git add readme.txt
		 
		 �ڶ�����������git commit����Git�����ļ��ύ���ֿ⣺
         $ git commit -m "wrote a readme file"

		 -m����������Ǳ����ύ��˵��
��.ʱ�⴩���
    
     git status ����鿴�ֿ⵱ǰ��״̬
	 git diff readme.txt �鿴�޸���ʲô���ݣ��鿴difference��
	 
	 1.�汾����
		git log  ������ʾ���������Զ���ύ��־����־�а����ύ�����ݺ��ύ��id����Ϣ��
		git log --pretty=oneline ����������Ϣ̫�࣬���Լ���--pretty=oneline����  
		
		git reset --hard^ �ص���һ���汾���ص���ȥ�İ汾��
		git reset --hard �汾id (�ص���ȥ�汾��δ���汾��ǰ����֪��δ���汾��id��ǰ��λ����)
		git reflog ��¼ÿһ������
		
		С��
		HEADָ��İ汾���ǵ�ǰ�汾����ˣ�Git���������ڰ汾����ʷ֮�䴩��ʹ������git reset --hard commit_id
		����ǰ����git log���Բ鿴�ύ��ʷ���Ա�ȷ��Ҫ���˵��ĸ��汾��
		Ҫ�ط�δ������git reflog�鿴������ʷ���Ա�ȷ��Ҫ�ص�δ�����ĸ��汾
	
		 
							
